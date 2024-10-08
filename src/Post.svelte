<script lang="ts">
    export let postHeader: string;
    export let posterName: string;
    export let postDate: number;
    export let postBody: string;

    export let shortenBody: number = -1;
</script>

<div class="bg-gray-100 m-2 px-4 py-3 rounded-sm">
    <div class="flex items-center">
        <p class="font-bold">{postHeader}</p>
        <p class="text-xs mx-2">Post By: {posterName}</p>
    </div>

    <div class="w-full h-[1px] bg-black"></div>
    
    {#if shortenBody == -1}
        <p>{postBody}</p>
    {:else}
        <p>{postBody.slice(0, Math.min(postBody.length, shortenBody))}...</p>
    {/if}

    <p>{new Date(postDate).toLocaleString()}</p>
</div>