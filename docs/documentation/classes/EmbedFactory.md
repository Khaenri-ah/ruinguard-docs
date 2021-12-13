# Embed Factory

Returns Embed

## Methods

### `.markdown(string)` { data-toc-label='markdown' }

This is a Markdown to Embed parser.

PARAMETER |    TYPE    |              DESCRIPTION
:-------: | :--------: | :-----------------------------------:
 string   | [Markdown] | The Markdown text to be sent as embed

**Examples:**

```javascript
interaction.markdown(`
  img:https://hi.test/image.png tm:${Date.now()}
tmb:https://hi.test/thumb.png clr:0x33aa22
aut:[leaf](https://leaf.moe)
::# [myBot](https://beatrice.leaf.moe)
some description

# field 1
some field value
can have multiple lines
#-inline field 2
this field is inline
#-inline field 3
so is this one
# this one isn't
they need a value though`)
```

### `.embed(string)` { data-toc-label='embed'}

PARAMETER |   TYPE   |         DESCRIPTION
:-------: | :------: | :--------------------------:
 string   | [String] | The text to be sent as embed

**Examples:**

```javascript
interaction.embed(`my current ping: ${interaction.client.ws.ping}ms`);
```

[markdown]: https://www.markdownguide.org/
[string]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String
