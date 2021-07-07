<script>
  import { onMount } from "svelte";
  export let userId;
  let writerName;

  onMount(async () => {
    const response = await fetch(
      `https://jsonplaceholder.typicode.com/users/${userId}`
    );
    const writer = await response.json();
    writerName = writer.name;
  });
</script>

{writerName}
