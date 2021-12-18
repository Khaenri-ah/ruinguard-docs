# Embeds

Along with regular implementation of Embeds as mentioned in [DJS guide about Embeds](https://discordjs.guide/popular-topics/embeds.html), RuinGuard Core also has a new way of making Embeds!

## Method 1

Usage:

```js
interaction.embed('This is a sample text');
```

## Method 2

This involves a custom markdown format.

Usage:

```js
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
  they need a value though
`)
```

## Notes

This is useful for 1 time messages.
