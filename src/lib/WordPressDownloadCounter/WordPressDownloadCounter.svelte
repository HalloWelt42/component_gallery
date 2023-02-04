<!--    let reponse = fetch('https://wordpress.org/wp-json/wporg/v1/core-downloads/6.1');-->
<script>
    import {onMount} from 'svelte';

    let count = 0;

    function convertToGermanFormat(value) {
        value.replace(',', '.');
        return value;
    }

    onMount(async () => {
        setInterval(async () => {
            const response = await fetch('https://wordpress.org/wp-json/wporg/v1/core-downloads/6.1');
            count = await response.json();
            count = count.replaceAll(',','.');
        }, 5000);
    });

    $:{
        console.log(count)
    }
</script>

<h1>
    WordPress Download Counter
    <br />
    {count}
</h1>


<style lang="scss">
  :global(html,body,#app) {
    display: flex;
    height: 100%;
    justify-content: center;
  }

  h1 {
    display: flex;
    font-size: 40px;
    color: #fff;
    text-align: center;
    align-items: center;
    margin-bottom: 40%;
  }
</style>