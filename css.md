# CSS

### Flexbox
* [🥕 Grid Garden](https://codepip.com/games/grid-garden/)
* [🐸 Flexbox Froggy](https://flexboxfroggy.com/)
* [A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
* [🎥 What The FlexBox?!](https://www.youtube.com/watch?v=Vj7NZ6FiQvo&list=PLu8EoSxDXHP7xj_y6NIAhy0wuCd4uVdid&index=1&ab_channel=WesBos)

## Tips and tricks
* [How to remove whitespaces between inline/inline-block elements](https://stackoverflow.com/questions/5078239/how-do-i-remove-the-space-between-inline-inline-block-elements)

### How to center an object

#### #1 way
```css
.container {
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%, -50%);
}
```

#### #2 way
```css
.parent {
	display: flex;
}
.child {
	margin: auto;
}
```