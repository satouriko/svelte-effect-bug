<svelte:options
  customElement={{
    tag: 'root-custom-element',
    props: {},
  }}
/>

<script lang='ts'>
  $host().addEventListener('change', () => {
    $host().querySelectorAll('my-custom-element').forEach((el: any) => {
      // Simple read causes $effect to trigger
      el.value;
    });
  })
</script>

<slot />

<style>
  :host {
    display: block;
  }
</style>
