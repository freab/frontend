<script lang="ts">
    import { onMount } from "svelte";
  
    export let path: string = ""; // Example: "/shop/women-tshirt"
    export let separator: string = " > ";
  
    let breadcrumbs: Array<{label: string, href?: string, isLast?: boolean, url?: string}> = [];
  
    onMount(() => {
      const parts = path.split("/").filter(Boolean);
      let accumulatedPath = "";
  
      breadcrumbs = parts.map((part, index) => {
        accumulatedPath += `/${part}`;
        return {
          label: part.replace("-", " "), // Replace hyphens with spaces
          url: accumulatedPath,
          isLast: index === parts.length - 1
        };
      });
    });
  </script>
  
  <!-- Breadcrumb Component -->
  <nav class="countainer mx-auto text-gray-600 text-sm p-4">
    <span>
      <a href="/" class="hover:underline text-gray-900">home</a>
      {#each breadcrumbs as crumb, i}
        <span> {separator} </span>
        {#if crumb.isLast}
          <span class="text-gray-900 font-semibold">{crumb.label}</span>
        {:else}
          <a href={crumb.url} class="hover:underline">{crumb.label}</a>
        {/if}
      {/each}
    </span>
  </nav>
  