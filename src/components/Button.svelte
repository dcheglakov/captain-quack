<script>
  export let type = "button";
</script>

<style>
  button[type="button"] {
    background-color: #282d30;
    color: #fff;
    border: none;
    border-radius: 2rem;
    padding: 0.5rem 1rem;
  }
  button[type="submit"] {
    color: #fff;
    font-weight: medium;
    background-color: #c4092f;
    text-transform: uppercase;
    border: none;
    border-radius: 0.25rem;
    padding: 0.5rem 1rem;
  }

  @media screen and (min-width: 45em) {
    button[type="button"] {
      background: none;
      color: #8b9497;
    }
    button[type="button"]:hover {
      color: #fff;
      background-color: #282d30;
    }
  }
</style>

<button {type}>
  <slot />
</button>
