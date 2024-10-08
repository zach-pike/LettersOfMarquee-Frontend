<script lang="ts">
    export let showHoverBar: boolean = true;
</script>

<div class="min-w-20 h-full flex items-center justify-center border-solid border-b-[1px] {showHoverBar ? "border-white" : "border-none"} hover:border-b-[3px] duration-75 mx-1">
    <slot></slot>
</div>