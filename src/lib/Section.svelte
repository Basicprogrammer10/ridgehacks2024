<script lang="ts">
  export let title: string;
  export let hidden: boolean = false;
  export let dark: boolean = false;
  let id = title.toLowerCase().replace(/\s/g, "-");
</script>

<div {id} style:display={hidden ? "none" : "block"} class:dark class="section">
  <h1>{title}</h1>
  <slot />
</div>

<style lang="scss">
  @use "sass:color";

  .section {
    border-radius: 8px;
    background-color: var(--foreground-color);
    padding: 20px;
    padding-top: 10px;
    margin-bottom: 20px;
    scroll-margin-top: 20px;
    color: #000;
    overflow-x: auto;

    &.dark {
      background-color: var(--alternate-foreground-color);
      color: #fff;
    }
  }

  @media (max-width: 600px) {
    .section {
      margin-bottom: 10px;
    }
  }
</style>
