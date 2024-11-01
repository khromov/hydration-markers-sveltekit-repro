<script>
    import stylizr from '@aftonbladet/stylizr';
  
    let { richText } = $props();
  
    function getNestedProps(child) {
      return {
        snippet: child.snippet,
        child: child.child ?? child,
        data: child.data,
      };
    }
  
    function createStylizerFunction(snippet) {
      return (child, _key, data) => ({
        snippet,
        child,
        data,
      });
    }
  
    const styles = {
      'style:em': createStylizerFunction(em),
      'style:strong': createStylizerFunction(strong),
      'link:external': createStylizerFunction(linkExternal),
      br: createStylizerFunction(br),
    };
  
    const stylizedOutput = [
      stylizr(styles)(richText.value, richText.markup),
    ].flat();
  </script>
  
  {#snippet text({ child })}
    {child}
  {/snippet}
  
  {#snippet em({ snippet = text, child })}
    <em>{@render snippet(getNestedProps(child))}</em>
  {/snippet}
  
  {#snippet strong({ snippet = text, child })}
    <strong>{@render snippet(getNestedProps(child))}</strong>
  {/snippet}
  
  {#snippet linkExternal({ snippet = text, child, data })}
    <a href={data?.uri} target="_blank"
      >{@render snippet(getNestedProps(child))}</a
    >
  {/snippet}
  
  {#snippet br()}
    <br />
  {/snippet}
  
  {#each stylizedOutput as output}
    {@render (output?.snippet ?? text)({
      snippet: output?.child?.snippet,
      child: output?.child ?? output,
      data: output?.data,
    })}
  {/each}
  