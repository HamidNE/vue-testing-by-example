##### 1. test mount component

```html
<template>
	<div>
		Hello world
	</div>
</template>

<script>
	export default {}
</script>
```

<details><summary><b>Answer</b></summary>

```javascript
import { shallowMount } from '@vue/test-utils';
import Component from './Component.vue';

const factory = () => {
	return shallowMount(Component);
};

describe('Component.vue', () => {
	test('should mount properly', () => {
		const wrapper = factory()
		expect(wrapper.vm).toBeTruthy();
	});
});
```
</details>

---

##### 2. test landing component (snapshot testing)

```html
<template>
	<div>
		Hello world
	</div>
</template>

<script>
	export default {}
</script>
```

<details><summary><b>Answer</b></summary>

```javascript
import { shallowMount } from '@vue/test-utils';
import Component from './Component.vue';

const factory = () => {
	return shallowMount(Component);
};

describe('Component.vue', () => {	
	test('renders correctly', () => {
		const wrapper = factory()
		expect(wrapper.element).toMatchSnapshot();
	});
});
```
</details>

---

##### 3. test normal component with props

```html
<template>
	<div>
		{{ title }}
	</div>
</template>

<script>
	export default {
		props: {
			title: {
				type: String,
				required: true,
			}
		}
	}
</script>
```

<details><summary><b>Answer</b></summary>

```javascript
import { shallowMount } from '@vue/test-utils';
import Component from './Component.vue';

const factory = () => {
	return shallowMount(Component, {
		propsData: { title: 'TITLE' }
	});
};

describe('Component.vue', () => {	
	test('should mount properly', () => {
		const wrapper = factory()
		expect(wrapper.vm).toBeTruthy();
	});
});
```
</details>

---