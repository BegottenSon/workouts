<script>
    import ToggleTople from "../components/ToggleTople.svelte"
    import ToggleFriction from "../components/ToggleFriction.svelte"
</script>

<style>
    main {
        display: flex;
        flex-flow: wrap;
        gap: 3em;
    }
</style>

<svelte:head><title>Workouts</title></svelte:head>
<main>
    <ToggleTople name="See-Saw Toggle" />
    <ToggleFriction />
</main>