<script>
    import { createEventDispatcher } from 'svelte';
    const dispatch = createEventDispatcher();

    let num1 = 0;
    let num2 = 0;
    let action  = '+';
    let result = 0;

    function calculate() {
        switch(action) {
            case '+':
                result = num1 + num2;
                break;
            case '-':
                result = num1 - num2;
                break;
            case '*':
                result = num1 * num2;
                break;  
            case '/':
                result = num1 / num2;
                break; 
        }
        dispatch('calculation', {result});
    } 
</script>

<main>
    <h1>Простенький калькулятор</h1>
    <input type="number" bind:value={num1} placeholder="Укажите первое число" />
    <select bind:value={action}>
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">*</option>
        <option value="/">/</option>
    </select>
    <input type="number" bind:value={num2} placeholder="Укажите второе число" />
    <button on:click={calculate}>Посчитать результат</button>
    {#if result !==0}
        <p>Результат: {result}</p>
    {/if}
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    input, select, button {
        margin: 10px;
        padding: 5px;
        border: 2px dotted #004623;
        border-radius: 4px;
    }

    button {
        background-color: #004623;
        color: aliceblue;
    }
</style>