<script lang="ts">
    import { createForm } from 'svelte-forms-lib';
    import { object, string } from 'yup';

    import 'modern-normalize/modern-normalize.css';

    export let name = 'kek';

    const CARD_NUMBER_MIN_LENGTH = 16;
    const CARD_NUMBER_MAX_LENGTH = 18;

    const CVV_LENGTH = 3;

    const { form, errors, state, handleChange, handleSubmit } = createForm({
        initialValues: {
            cardNumber: "",
            cardholderName: "",
            expireDate: "",
            cvv: "",
        },
        validationSchema: object().shape({
            cardNumber: string().min(CARD_NUMBER_MIN_LENGTH).max(CARD_NUMBER_MAX_LENGTH).required(),
            cardholderName: string().matches().required(),
            expireDate: string().required(),
            cvv: string().length(CVV_LENGTH).required(),
        }),
        onSubmit: values => {
            console.log(JSON.stringify(values));
        }
    });
</script>

<main>
    <h1>Hello {name}!</h1>

    <div class="form-wrapper">
        <input
                id="cardNumber"
                name="cardNumber"
                placeholder="Card number"
                on:change={handleChange}
                on:blur={handleChange}
                bind:value={$form.cardNumber}
        />

        {#if $errors.cardNumber}
            <small>{$errors.cardNumber}</small>
        {/if}

        <input
                id="cardholderName"
                name="cardholderName"
                placeholder="Cardholder Name"
                on:change={handleChange}
                on:blur={handleChange}
                bind:value={$form.cardholderName}
        />

        {#if $errors.cardholderName}
            <small>{$errors.cardholderName}</small>
        {/if}

        <input
                id="expireDate"
                name="expireDate"
                placeholder="Expiration Date"
                on:change={handleChange}
                on:blur={handleChange}
                bind:value={$form.expireDate}
        />

        {#if $errors.expireDate}
            <small>{$errors.expireDate}</small>
        {/if}

        <input
                id="cvv"
                name="cvv"
                placeholder="CVV"
                on:change={handleChange}
                on:blur={handleChange}
                bind:value={$form.cvv}
        />

        {#if $errors.cvv}
            <small>{$errors.cvv}</small>
        {/if}

        <button on:click={handleSubmit}>submit</button>
    </div>
</main>

<style>
    main {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 2em;
        font-weight: 100;
    }

    .form-wrapper {
        width: 360px;
        display: flex;
        flex-direction: column;
        gap: 8px;
    }
</style>