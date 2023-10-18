<script>
    import Modal from "../components/Modal.svelte";
    const client_id = import.meta.env.VITE_QUOTES_API_KEY
    let visible = false
    let quote = null
    let getQuote = async (type)=>{
        let quote
        const endpoint = `https://api.api-ninjas.com/v1/quotes?category=${type}`
        const res = await fetch(endpoint, {
            headers: { 'X-Api-Key': client_id},
            
        }).then((res => res.json()))
        .then(quoteRes => quote = quoteRes)
        return quote
    }
</script>
<div class="text-white flex flex-col gap-9 mx-auto my-10 w-9/12">
    
    {#if visible}
        {#await quote}
            
        {:then quote} 
            <Modal bind:visible quote = {quote}/> 
        {/await}
        
    {/if}
    <h8 class="text-8xl font-bold mb-5 text-violet-500">My rules</h8>
    <h1 class="text-xl">Remember: Rules are absolute. These are the guiding statements of your whole life. Fail to them and you would have failed yourself</h1>

    <ol class="list-decimal text-xl list-inside pl-5 space-y-4 text-justify">

        <li on:click={() =>{quote = getQuote('fitness');visible = true }} class=" hover:text-yellow-400 duration-200">Your body is a temple, and you must take care of it as one. Nutrition, exercise, flexibility, and posture are the rulers of the temple; don’t let your temple ruin and if it’s ruined then take a shovel and build from the ground. Remember, the body is the home of your mind and soul.</li>
        <li on:click={() =>{quote = getQuote('intelligence');visible = true }} class=" hover:text-yellow-400 duration-200">As well as you nurture your body you MUST nurture your mind. Never stop learning not because you want to be a smartass but because knowledge is invaluable. Never brag about your knowledge and let your actions talk for you.</li>
        <li on:click={() =>{quote = getQuote('freedom');visible = true }} class=" hover:text-yellow-400 duration-200">Finally nurture your soul. Your body and mind can be easily feed but your soul will need a different type of sustenance. Play the violin, meditate, read philosophy, or simply go for a walk to have some introspective. </li>
        <li on:click={() =>{quote = getQuote('happiness');visible = true }} class=" hover:text-yellow-400 duration-200">Take a breath once a week. You know you deserve it and don’t try to negotiate with yourself. Resting is vital to keep a healthy body, mind, and soul.</li>
        <li on:click={() =>{quote = getQuote('family');visible = true }} class=" hover:text-yellow-400 duration-200">Remember to talk to people you love. Just because you can be alone does not mean you have to. Many people love you and accept you no matter what so feel the love that they give you.</li>
        <li on:click={() =>{quote = getQuote('money');visible = true }} class=" hover:text-yellow-400 duration-200">Never spend more money than your earnings. Always save money and invest it.</li>
        <li on:click={() =>{quote = getQuote('success');visible = true }} class=" hover:text-yellow-400 duration-200">Avoid easy dopamine. You can have fun with it, but it can be highly addictive. From time to time there will be situations where it is inevitable so don’t feel guilty: Enjoy and then let go.</li>
        <li on:click={() =>{quote = getQuote('success');visible = true }} class=" hover:text-yellow-400 duration-200">Check your own achievements and never other’s. The only person you are competing against is yourself. You are the person you must surpass every day. Tomorrow you will know more, lift more, feel more, and love more than yesterday.</li>
        <li on:click={() =>{quote = getQuote('failure');visible = true }} class=" hover:text-yellow-400 duration-200">Detach from the idea of total control. You will never be able to control many aspects outside of your own life and that’s okay. Only worry of the matters that you can </li>
        <li on:click={() =>{quote = getQuote('love');visible = true }} class=" hover:text-yellow-400 duration-200">Love yourself.</li>
        
    </ol>
</div>
