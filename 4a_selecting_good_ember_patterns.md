# \<.SELECT\>ing Good Ember Patterns

given by [@brnnbrn](https://twitter.com/brnnbrn)


Sorry for those looking at this, I had to type as fast as I could to keep up!

### What's the problem with Ember's select view?

* Two-way Bindings
* DOM issues(such as having disabled options)

## Better SELECT
1. Real HTML
2. Data Down, Actions Up
3. Cool New Ember Features


A pretty normal select field:
```html
<select>
  <option value="">select an option</option>

  {{#each language as |language|}}
    <option value={{language.code}}>
      {{language.name}}
    </option>
  {{/each}}
</select>
```

We want the initial selection to trigger an onChange event.(actions up)

```html
<select onchange={{action "languageDidChange" value="target.value"}}>
  <option value="">select an option</option>

  {{#each language as |language|}}
    <option value={{language.code}}>
      {{language.name}}
    </option>
  {{/each}}
</select>
```

```javascript
actions: {
  languageDidChange() {
    this.sendAction('languageDidChange', selection);
  }
}
```

Data-down

```html
<select onchange={{action "languageDidChange" value="target.value"}}>
  <option value="">select an option</option>

  {{#each language as |language|}}
    <option value={{language.code}} selected={{is-equal language selectedLanguage}}>
      {{language.name}}
    </option>
  {{/each}}
</select>
```

Dynamic Attributes have been in since 1.10, `bind-attr` was deprecated in 1.13.

#### Disabled Options

export default thing({
  name: DS.attr()
  isYellow: Ember.computed.equal('colour', 'yellow')
});


##### Flexible :)
##### Reusable :(

## Components

<select onchange

// controllers/some-route.js
```javascript
actions: {
  fruitDidChange(value) { // deal with it };
}
```

But Closure Actions make the bubble-up better!

// templates/some-route.hbs
```html
{{fruit-select onchange=(action "updateFruit")}}
```
// controllers/some-route.js
```javascript
actions: {
  updateFruit(fruit) { //deal with it }
}
```

Data-down for component:
```html
{{#each fruits as |fruit|}}
  <option
    disabled={{fruit.isYellow}}
    selected={{is-equal fruit selectedFruit}}
    value={{fruit.id}}>
    {{fruit.name}}
  </option>
{{/each}}
```

Wait, what about isYellow? Crap, handling the disabled key will be hard.

#### But, the {{GET}} Helper!

```html
{{#each fruits as |fruit|}}
disabled={{get fruit disabledKey}}
```

```html
{{fruit-select disabledKey="isRed"}}
```

What about two-way binding?

##### Enter, the Mut Helper(avail in 1.13 and up)
```html
{{fruit-select
  onchange=(action (mut selectedFruit))
  fruits=fruits
  selectedFruit=selectedFruit}}
```

<select onchange={{action 'fruitDidChange' value='target.value'}}>

```html
actions: {
  fruitDidChange(value) {
    let selection = this.get('fruits').findBy('id', +value);
    this.get('onchange')(selection)
  }
}
```

talks.brennaobrien.com/ember-select


## Give `ember-ted-select` a try! It doesn't handle everything, but it's pretty solid.

Slides: http://talks.brennaobrien.com/ember-select/
