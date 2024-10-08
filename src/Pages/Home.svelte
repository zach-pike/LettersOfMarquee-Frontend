<script lang="ts">
    import Post from '../Post.svelte';

    interface Post {
        postHeader: string;
        posterName: string;
        postDate: number;
        postBody: string;
    }

    let oldPosts: Post[] | null = null;
    let newPosts: Post[] | null = null;

    fetch("http://localhost:3000/posts/old").then(v => v.json()).then(d => oldPosts = d);
    fetch("http://localhost:3000/posts/new").then(v => v.json()).then(d => newPosts = d);
</script>

<div class="m-2 px-2 py-1 bg-white md:w-2/3 lg:w-3/4 overflow-y-scroll">
    <p class="text-3xl">Todays Story...</p>

    {#if newPosts != null}
        {#if newPosts.length == 0}
            <p>No posts from today yet...</p>
            <p>Heres some other posts to read</p>

            {#if oldPosts == null || oldPosts.length == 0}
                <p>Nothing to see here</p>
            {:else}
                {#each oldPosts.slice(0, Math.min(oldPosts.length, 3)) as post}
                    <Post {...post} />
                {/each}
            {/if}

        {:else}
            {#each newPosts as post}
                <Post {...post} />
            {/each}
        {/if}
    {:else}
        <p>Loading</p>
    {/if}
</div>

<!-- side content container -->
<div class="m-2 bg-white md:w-1/3 lg:w-1/4 overflow-y-scroll">
    <div class="w-full flex flex-col items-center px-2 py-1">
        <p class="text-3xl font-bold">Other Stories</p>

        <!-- divider -->
        <div class="w-full h-[1px] bg-gray-600 m-2"></div>

        {#if oldPosts == null || oldPosts.length == 0}
            <p>No posts from today yet...</p>
        {:else}
            {#each oldPosts as post}
                <Post {...post} shortenBody={150} />
            {/each}
        {/if}
    </div>
</div>