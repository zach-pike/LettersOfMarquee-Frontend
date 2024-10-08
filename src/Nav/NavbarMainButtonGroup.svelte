<script lang="ts">
    import NavbarItem from "./NavbarItem.svelte";
    import NavbarSpacer from "./NavbarSpacer.svelte";

    export let click: () => void = ()=>{};
</script>
<div class="h-full w-full hidden sm:flex">
    <slot></slot>
</div>

<div class="h-full w-full flex sm:hidden">
    <NavbarSpacer />

    <NavbarItem showHoverBar={false}>
        <button class="" on:click={click}>
            <!-- svelte-ignore a11y-missing-attribute -->
            <img src="menu.svg" />
        </button>
    </NavbarItem>
</div>