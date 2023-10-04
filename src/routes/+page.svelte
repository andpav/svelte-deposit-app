<script lang="ts">
    import 'modern-normalize/modern-normalize.css';

    export let name = 'kek';

    let cardNumber = '';
    let cardholderName = '';
    let expireDate = '';
    let cvv = '';

    const submit = () => {
        const result = {
            cardNumber,
            cardholderName,
            expireDate,
            cvv
        }

        console.log(result, ' !!!!!!')
    }
</script>

<main>
    <h1>Hello {name}!</h1>

    <div class="form-wrapper">
        <input bind:value={cardNumber} placeholder="Card number"/>
        <input bind:value={cardholderName} placeholder="Cardholder Name"/>
        <input bind:value={expireDate} placeholder="Expiration Date"/>
        <input bind:value={cvv} placeholder="CVV"/>

        <button on:click={submit}>submit</button>
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