# react-native-style-guide

### Размешать стили так как они идут в потоке

```ts
<View style={styles.list}>
  <View style={styles.item}>item...</View>
</View>
```

**Bad:**

```ts
item: {
  ...
}, 

list: {
  ...
}
```

**Good:**

```ts
list: {
  ...
}, 

item: {
  ...
}
```

### Ильпользовать меньше оберток

Если обертка не несет функциональной необходимости, например для разделения или использования стилей, стоит отказаться от нее.

**Bad:**

```ts
<View key={index}>
  <View style={…}>
	  <Text>text</Text>
  </View>
</View>
```

**Good:**

```ts
<View style={…} key={index}>
  <Text>text</Text>
</View>
```

### Различать внутренний и внешние отступы

Внутренний - padding и внешние - margin отступы можно легко взаимозаменять, при этом внешне результат чаще всего будет идентичен. Но это совершенно разные вещи и их нужно различать. Ваш помошник - это дизайн и компонентый подход. Но легче всего запомнить такое правило: padding для элемента, и отталкивания контента от внутренних стенок, а margin, что бы отталкивать элементы друг от друга.

В данном контексте компонент list будет использоваться в других местах и использовать margin не целесообразно, так как необходимо добиться именно внетреннего отспута элементов. А margin в данном случае лучше использовать для отталкивания элементов или отступа всего компонента list.

```ts
<View style={styles.list}>
  <View style={styles.item}>...></View>
  <View style={styles.item}>...</View>
  <View style={styles.item}>...</View>
</View>
```

**Bad:**

```ts
list: {
  marginVertical: 10,
  marginHorizontal: 10
}
```

**Good:**

```ts
list: {
  paddingVertical: 10,
  paddingHorizontal: 10
  marginBottom: 8
},

item: {
  paddingVertical: 10,
  paddingHorizontal: 10,
  marginBottom: 4
}
```

### G

```ts
<View style={styles.list}>
  <View style={styles.item}>item...</View>
</View>
```

**Bad:**

```ts
item: {
  ...
}, 

list: {
  ...
}
```

**Good:**

```ts
list: {
  ...
}, 

item: {
  ...
}
```

### Избегать отрицательных значений margin

Соблазн быстро решить задачу через отрицательные значения margin велик, но чаще всего в дальнешей перспективе это приносит больше проблем. Так при компонентном подходе, отрицательное значение сыграет злую шутку и элемент уплывет за указанные границы контенера. Несомненно отрицательный margin иногда необходим. В данном случае нужно быть предельно внимательным в рачетах.

```ts
<View style={styles.list}>
  <View style={styles.item}>item...</View>
</View>
```

**Bad:**

```ts
list: {
  paddingLeft: 10
},

item: {
  marginLeft: -10
}
```

**Good:**

```ts
list: {
  paddingLeft: 0
}
```
