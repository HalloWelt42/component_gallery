<script>
    // https://codepen.io/Unleashed-Design/pen/oNMeBPP
    export let cards = [0, 1, 2, 3, 4, 5];
    let card = [];

    function mousemove(e) {
        const rect = card.getBoundingClientRect();
        const x = e.target.clientX - rect.left;
        const y = e.target.clientY - rect.top;

        card.style.setProperty("--xPos", `${x}px`);
        card.style.setProperty("--yPos", `${y}px`);
    }

</script>

<div class="cards">
    {#each cards as c}
        <div class="card" on:mouseover={mousemove}>
            <div class="card-content"></div>
        </div>
    {/each}
</div>

<style lang="scss">
  $prime: #ff6e48;
  $ciBlue: #00fff1;
  $ciRed: #ff00aa;
  $ciWhite: #ffffff;
  $ciGreen: #46fcb4;
  $ciSecond: #0c1016;

  $roboto: "Roboto";

  :global(body,html) {
    background: #114;
  }


  body,
  html {
    width: 100%;
    min-height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-color: $ciSecond;
    font-size: 20px;
    margin: 0;
    padding: 0;
    color: $ciWhite;
    font-family: $roboto;
    overflow-x: hidden;
  }

  * {
    box-sizing: border-box;
  }

  // Tutorial Start

  .cards {
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
    width: 90%;
    padding: 2rem;

    &:hover {
      .card {
        background: radial-gradient(
                        100rem circle at var(--xPos) var(--yPos),
                        rgba($ciBlue, 0.4),
                        transparent 15%
        );
      }
    }

    .card {
      width: 20rem;
      height: 15rem;
      background: radial-gradient(
                      150rem circle at 0 0,
                      rgba($ciBlue, 0),
                      transparent 0%
      );
      border-radius: 0.5rem;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      transition: all 0.15s;

      &:hover {
        transform: scale(0.97);

        &::before {
          opacity: 1;
        }
      }

      &::before {
        content: "";
        height: 100%;
        width: 100%;
        position: absolute;
        top: 0;
        left: 0;
        border-radius: inherit;
        background: radial-gradient(
                        60rem circle at var(--xPos) var(--yPos),
                        rgba($ciBlue, 0.1),
                        transparent 35%
        );
        opacity: 0;
        transition: all 0.15s ease-in-out;
      }

      .card-content {
        background-color: #13161c;
        border-radius: inherit;
        transition: all 0.25s;
        height: calc(100% - 0.1rem);
        width: calc(100% - 0.1rem);
      }
    }
  }

</style>