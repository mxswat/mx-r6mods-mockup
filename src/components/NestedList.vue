<template>
  <div>
    <template v-for="(sourcecat, category) in source">
      <div class="source_x_cat" v-bind:key="category">
        <span class="category_name" @click="clicked(category)">
          {{category}}
          <span class="arrow-down"></span>
        </span>
        <div class="element-container" v-bind:class="{ 'd-none': !isOpenElementCat[category] }">
          <span class="element-name" v-for="elementName in sourcecat" v-bind:key="elementName">
            <span>{{elementName}}</span>
            <label class="primary-label" :for="elementName + 'primary'">
              <input
                type="radio"
                :id="elementName + 'primary'"
                name="primary-name"
                :value="elementName"
              />
              <span class="primary-name">Primary</span>
            </label>
            <label class="secondary-label" :for="elementName + 'secondary'">
              <input
                type="radio"
                :id="elementName + 'secondary'"
                name="secondary-name"
                :value="elementName"
              />
              <span class="secondary-name">Secondary</span>
            </label>
          </span>
        </div>
      </div>
    </template>
  </div>
</template>

<script>
import Vue from "vue";
export default {
  props: ["source"],
  name: "NestedList",
  data() {
    return {
      isOpenElementCat: {}
    };
  },
  created() {
    const keys = Object.keys(this.source);
    for (let index = 0; index < keys.length; index++) {
      Vue.set(this.isOpenElementCat, keys[index], false);
    }
  },
  methods: {
    clicked(category) {
      this.isOpenElementCat[category] = !this.isOpenElementCat[category];
    }
  }
};
</script>

<style lang="scss">
.source-tile {
  text-transform: uppercase;
  color: white;
  font-weight: bold;
  font-size: 20px;
  display: block;
  margin-bottom: 20px;
}

.category_name {
  text-transform: uppercase;
  color: #ff5722;
  font-weight: bold;
  cursor: pointer;
  display: flex;
  border-bottom: 1px solid gray;
}

.source_x_cat {
  margin-bottom: 8px;
}

.element-container {
  display: flex;
  flex-direction: column;
  padding: 8px;
}

.element-name {
  display: flex;
}

.primary-label {
  margin-left: auto;
  margin-right: 8px;
}

.arrow-down {
  height: 14px;
  width: 14px;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='14' fill='white' height='10' role='presentation' class='vs__open-indicator'%3E%3Cpath d='M9.211364 7.59931l4.48338-4.867229c.407008-.441854.407008-1.158247 0-1.60046l-.73712-.80023c-.407008-.441854-1.066904-.441854-1.474243 0L7 5.198617 2.51662.33139c-.407008-.441853-1.066904-.441853-1.474243 0l-.737121.80023c-.407008.441854-.407008 1.158248 0 1.600461l4.48338 4.867228L7 10l2.211364-2.40069z'%3E%3C/path%3E%3C/svg%3E");
  background-repeat: no-repeat;
  margin-left: auto;
  background-position: bottom;
}

.d-none {
    display: none;
}
</style>