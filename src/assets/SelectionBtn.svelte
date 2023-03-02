<script lang="ts">
    export let text: String;
    let activationChar: String = Array.from(text)[0].toLowerCase();
    export let stagger: number;

    import { fly } from 'svelte/transition';

    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    let inputShortcut = (e: KeyboardEvent) => {
        if (e.key === activationChar) {
            dispatch('shortcut', {
                key: e.key
            });
        }
    }

</script>

<svelte:body on:keypress={inputShortcut}/>

<button transition:fly="{{ y: 50, duration: 500, delay: stagger }}"><p>{text}</p><img class="icon" alt="SVG for {text}" src="../../public/{text}.svg"></button>

<style>
    button {
        display: flex;
        justify-content: space-between;
        align-items: center;
        font-size: 2rem;
        outline: none;
        border: none;
        border-radius: 10px;
        min-width: 350px;
        padding: 5px 20px;
    }

    button:hover {
        filter: brightness(85%);
    }

    p::first-letter {
        text-decoration-line: underline;
        text-decoration-color: black;
    }

    .icon {
        width: 30px;
        height: 30px;
    }

</style>
