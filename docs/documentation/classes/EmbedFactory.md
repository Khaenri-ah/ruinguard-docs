# EmbedFactory

Creates embeds

## Methods

### `.markdown(string)` { data-toc-label='markdown' }

This is a Markdown to Embed parser.

PARAMETER |    TYPE    |              DESCRIPTION
:-------: | :--------: | :-----------------------------------:
 string   |  [String]  | The Markdown text to be sent as embed

**Returns: [MessageContent]**

**Examples:**

```javascript
factory.markdown(`
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
  they need a value though
`)
```

### `.create(string)` { data-toc-label='embed'}

PARAMETER |   TYPE   |         DESCRIPTION
:-------: | :------: | :--------------------------:
 string   | [String]\|[Object] | The text to be sent as embed description, or an embed object

 **Returns: [MessageContent]**

**Examples:**

```javascript
factory.create(`my current ping: ${interaction.client.ws.ping}ms`);
```

[MessageContent]: MessageContent.md
[string]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String
[Object]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object
