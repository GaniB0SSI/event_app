<script>
    const { message } = $props();
</script>

<div>
    <p>{message}</p>
</div>

<style>
    div {
        margin-top: 1rem;
        background: #ffcccc;
        color: #900;
        padding: 0.75rem;
        border-radius: 5px;
        text-align: center;
        font-weight: bold;
    }
</style>