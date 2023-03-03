<script lang="ts">
    import SelectionBtn from "./assets/SelectionBtn.svelte";
    import Typewriter from 'svelte-typewriter'

    let menu = [
        { id: 1, name: 'Movement', sub: [{name: 'A'},{name: 'B'},{name: 'C'}] },
        { id: 2, name: 'Replacement' },
        { id: 3, name: 'Actions' },
    ];

    let changeScreen = (e: CustomEvent) => {
        switch (e.detail.key) {
            case 'm':
                console.log('doing movement');
                break;
            case 'r':
                console.log('doing replacement');
                break;
            case 'a':
                console.log('doing actions');
                break;
        }
    }

    function removeMenu() {
    const intervalId = setInterval(() => {
      if (menu.length > 0) {
            menu.pop();
            menu = menu;
      } else {
        clearInterval(intervalId);
      }
    }, 500);
  }

</script>

<main>
    <Typewriter>
        <h1>What would you like to practice...</h1>
    </Typewriter>
    <section>
        {#each menu as btn (btn.id)}
            <SelectionBtn on:shortcut={changeScreen} text={btn.name} stagger={0}/>
        {/each}
    </section>
    <button on:click={removeMenu}>Click me</button>
</main>

<style>
    main {
        max-width: 40%;
    }

    section {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        gap: 1em;
        text-align: left;
    }

    h1 {
        font-size: 3rem;
        margin-bottom: 1em;
    }

</style>
