<script>
    import { fade } from 'svelte/transition';
export let showDrop;
</script>

{#if showDrop}
<div in:fade out:fade on:click|self class="back-drop">
    <div class="mainModal">
        <slot></slot>
    </div>
</div>

{/if}

<style>
    .back-drop{
        width: 100vw;
        height: 100vh;
        position: fixed;
        background: rgba(0, 0, 0, 0.8);
    }

    .mainModal{
        max-width: 400px;
        background: white;
        margin: 10% auto;
        border-radius: 10px;
        padding: 10px
    }
</style>
