<script>
    import Button from "./Button.svelte";
    import Card from "./Card.svelte";
    import RatingSelect from "./RatingSelect.svelte";

    let text = "";
    let buttonDisabled = true;
    let rating = 0;
    let message = "";
    const minLength = 5;

    const handleInput = () => {
        if (text.trim().length > minLength) {
            buttonDisabled = false;
            message = "";
        } else {
            message = `Please enter at least ${minLength} characters`;
            buttonDisabled = true;
        }
    };
</script>

<Card>
    <header>
        <h2>How would you rate your service with us?</h2>
    </header>
    <form>
        <RatingSelect />
        <div class="input-group">
            <input
                type="text"
                bind:value={text}
                on:input={handleInput}
                placeholder="Enter your feedback"
            />
            <Button type={"submit"} disabled={buttonDisabled}>Send</Button>
        </div>
        {#if message}
            <div class="message">
                {message}
            </div>
        {/if}
    </form>
</Card>

<style>
    header {
        max-width: 400px;
        margin: auto;
    }

    header h2 {
        font-size: 22px;
        font-weight: 600;
        text-align: center;
    }

    .input-group {
        display: flex;
        flex-direction: row;
        border: 1px solid #ccc;
        padding: 8px 10px;
        border-radius: 8px;
        margin-top: 15px;
    }

    input {
        flex-grow: 2;
        border: none;
        font-size: 16px;
    }

    input:focus {
        outline: none;
    }

    .message {
        padding-top: 10px;
        text-align: center;
        color: rebeccapurple;
    }
</style>
