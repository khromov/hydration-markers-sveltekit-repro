<script lang="ts">
  import Stylizr from "$lib/Stylizr.svelte";

  const richText = {
    text: "This is a formatting test using Svelte to demonstrate rich text styling capabilities. When working with modern web frameworks like Svelte, we can easily implement complex text formatting patterns. The Stylizr component makes it straightforward to apply various styles like italics, bold text, and hyperlinks throughout your content. This creates a more engaging and dynamic reading experience.",
    markup: [
      {
        length: 4,
        offset: 0,
        type: "style:em",
      },
      {
        length: 10,
        offset: 10,
        type: "style:strong",
      },
      {
        length: 5,
        offset: 15,
        type: "style:em",
      },
      {
        length: 6,
        offset: 32,
        type: "link:external",
        uri: "https://www.svelte.dev/",
      },
      {
        length: 31,
        offset: 39,
        type: "style:em",
      },
      {
        length: 6,
        offset: 108,
        type: "link:external",
        uri: "https://www.svelte.dev/",
      },
      {
        length: 18,
        offset: 147,
        type: "style:strong",
      },
      {
        length: 46,
        offset: 189,
        type: "style:em",
      },
      {
        length: 41,
        offset: 236,
        type: "style:strong",
      }
    ],
    value: "This is a formatting test using Svelte to demonstrate rich text styling capabilities. When working with modern web frameworks like Svelte, we can easily implement complex text formatting patterns. The Stylizr component makes it straightforward to apply various styles like italics, bold text, and hyperlinks throughout your content. This creates a more engaging and dynamic reading experience."
  };
</script>

<div>
  <Stylizr {richText} />
</div>