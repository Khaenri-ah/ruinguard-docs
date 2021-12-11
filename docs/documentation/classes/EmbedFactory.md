# Embed Factory

.markdown()

This is a Markdown to Embed parser.

Usage:

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
