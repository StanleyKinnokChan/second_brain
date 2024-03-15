
# ✅ Checkbox

- [x] here is a checked checkbox
- [ ] here is a unchecked checkbox

# 🗒️ Banners/ Callouts

see [here](https://help.obsidian.md/Editing+and+formatting/Callouts)

>[!success] Success / Proofs
>Success sessions show proofs. Being able to prove statements is a strong metric of success

>[!info] Info / Notation
>Info sections describe the notation used. They are essential to understand the rest of the note, but can be ignored by the familiar reader. As such they are collapsed by default.

>[!tip] Tips / Intuition
> Tips section provide intuition about the rest of the note

>[!quote]
> Quotes to external webpages

> [!warning] Ongoing Makeover
> Note that as of November 2023, I'm in the process of giving the Notkesto a makeover with proper navigation. 

> [!example] example
> example

You can make a callout foldable by adding -/+ directly after the type identifier. E.g

> [!faq]- Are callouts foldable?
> Yes! In a foldable callout, the contents are hidden when the callout is collapsed.


# Others:
https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax
## Strikethrough

Need to strike ~~some text~~? Use `<s>this</s>` to strike it out.

### Underline

If you need to quickly underline an item in your notes, you can use `<u>Example</u>` to create your underlined text.

### Embed web pages

Learn how to use the [iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) HTML element to embed web pages in your notes.
```html
<iframe src="INSERT YOUR URL HERE"></iframe>
```

To embed a YouTube video, use the same Markdown syntax as [external images](https://help.obsidian.md/Editing+and+formatting/Basic+formatting+syntax#External images):

```md
![](https://www.youtube.com/watch?v=NnTvZWp5Q7o)
```

## Footnotes

You can add footnotes to your notes using the following syntax:

This is a simple footnote[^1].

[^1]: This is the referenced text.

You can also use inline footnotes. ^[This is an inline footnote.]

### Comments
You can add comments by wrapping text with `%%`. Comments are only visible in Editing view.

```md
This is an %%inline%% comment.

%%
This is a block comment.

Block comments can span multiple lines.
%%
