<script lang="ts">
    import SelectionBtn from "./assets/SelectionBtn.svelte";
    import Typewriter from 'svelte-typewriter'

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

</script>

<main>
    <Typewriter>
        <h1>What would you like to practice...</h1>
    </Typewriter>
    <section>
        <SelectionBtn on:shortcut={changeScreen} text={"Movement"} stagger={0}/>
        <SelectionBtn on:shortcut={changeScreen} text={"Replacement"} stagger={75}/>
        <SelectionBtn on:shortcut={changeScreen} text={"Actions"} stagger={150}/>
    </section>
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
