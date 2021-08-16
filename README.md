# swiper-tabs-demo

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Run your tests

```
npm run test
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

# vue-awesome-swiper 实现 tab 切换效果

[![](https://tva1.sinaimg.cn/large/008i3skNly1gtiqp6czz9j60n40ayglv02.jpg)](https://liuzhenghe30265.github.io/swiper-tabs-demo)

[Github](https://github.com/liuzhenghe30265/swiper-tabs-demo.git)

## vue-awesome-swiper 3.x

安装 vue-awesome-swiper 3.x 时会自动安装 swiper 4.x

```bash
npm install vue-awesome-swiper@3.1.3 --save
```

```html
<template>
	<div id="app">
		<h5swiper
			ref="swiperTitle"
			class="swiper-title"
			:options="swiperOptionTitle"
			:auto-update="true"
			:auto-destroy="true"
			:delete-instance-on-destroy="true"
			:cleanup-styles-on-destroy="true"
		>
			<swiper-slide
				v-for="(item, index) of tabListData"
				ref="swiperSlideItem"
				:key="'name' + index"
				:iname="item.name"
				class="swiper-slide-title"
			>
				<div
					class="tab-name"
					:class="{ active: index === swiperActiveIndex }"
					@click="handleSlidClickFun(index)"
				>
					{{ item.name }}
				</div>
			</swiper-slide>
		</h5swiper>
		<h5swiper
			ref="swiperContent"
			class="swiper-content"
			:options="swiperOptionContent"
			:auto-update="true"
			:auto-destroy="true"
			:delete-instance-on-destroy="true"
			:cleanup-styles-on-destroy="true"
		>
			<swiper-slide
				v-for="(item, index) of tabListData"
				:key="'content' + index"
				class="swiper-slide-content"
			>
				{{ item.name }}
			</swiper-slide>
		</h5swiper>
	</div>
</template>

<script>
//  vue-awesome-swiper 官网 https://github.surmon.me/vue-awesome-swiper/
import { swiper as h5swiper, swiperSlide } from 'vue-awesome-swiper'
import 'swiper/dist/css/swiper.css'
export default {
	components: {
		h5swiper,
		swiperSlide,
	},
	data() {
		const _this = this
		return {
			swiperActiveIndex: 0,
			titleActive: '',
			swiperOptionContent: {
				slidesPerView: 'auto',
				on: {
					slideChangeTransitionStart: function() {
						_this.swiperActiveIndex = this.activeIndex
						_this.swiperTitle.slideTo(this.activeIndex, 500, false)
					},
				},
			},
			swiperOptionTitle: {
				slidesPerView: 'auto',
				freeMode: true,
			},
			tabListData: [
				{
					name: '直播',
				},
				{
					name: '推荐',
				},
				{
					name: '追番',
				},
				{
					name: '热门',
				},
				{
					name: '影视',
				},
				{
					name: '奥运',
				},
				{
					name: '建党百年',
				},
			],
		}
	},
	computed: {
		swiperContent() {
			return this.$refs.swiperContent.$el.swiper
		},
		swiperTitle() {
			return this.$refs.swiperTitle.$el.swiper
		},
	},
	mounted() {},
	methods: {
		handleSlideToFun(index) {
			this.swiperActiveIndex = index
			this.swiperContent.slideTo(index, 500, false)
			this.swiperTitle.slideTo(index, 500, false)
		},
		handleSlidClickFun(index) {
			this.handleSlideToFun(index)
		},
	},
}
</script>

<style lang="scss">
.swiper-slide-title {
	width: auto !important;
	.tab-name {
		padding: 10px;
		&.active {
			color: #2ea9fe;
		}
	}
}
.swiper-slide-content {
	padding: 10px;
}
</style>
```

## vue-awesome-swiper 4.x

使用 vue-awesome-swiper 4.x，需要同时安装 vue-awesome-swiper 和 swiper

```bash
npm install swiper vue-awesome-swiper --save
```

package.json

```json
"dependencies": {
	"swiper": "^6.8.1",
	"vue-awesome-swiper": "^4.1.1",
},
```

使用方式和 vue-awesome-swiper 3.x 相同，引用方式差异：

```js
import { Swiper, SwiperSlide } from "vue-awesome-swiper";
import "swiper/swiper-bundle.css";
export default {
  components: {
    Swiper,
    SwiperSlide,
  },
};
```
