<svelte:options
  customElement={{
    tag: 'my-custom-element',
    props: {
      value: { type: 'String', reflect: true },
    },
  }}
/>

<script lang='ts'>
  let {
    value = '',
  }: {
    value: string;
  } = $props();

  $effect(() => {
    console.warn($host(), '$effect triggered!!!')
    $host().dispatchEvent(new CustomEvent('change', { bubbles: true, detail: { value } }));
  })

  function oninput(e: Event) {
    const target = e.target as HTMLInputElement;
    value = target.value;
  };
</script>

<input
  {value}
  oninput={e => oninput(e)}
/>

<style>
  :host {
    display: inline-block;
  }
</style>
