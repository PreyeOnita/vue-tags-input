<template lang="html">
  <div class="slot-docs-item">
    <div class="name">
      <span class="value code">{{ item.slot }}</span>
    </div>
    <p class="description meta" v-if="item.description">
      {{ item.description }}
    </p>
    <div class="slot-scope meta" v-if="item.props && item.props.length">
      <span class="label big">Slot Scope</span>
      <ul>
        <li v-for="(prop, index) in item.props" :key="index">
          <div>
            <span class="label">Name</span>
            <span class="code">{{ prop.name }}</span>
          </div>
          <div>
            <span class="label" v-if="prop.description">Description</span>
            <span>{{ prop.description }}</span>
          </div>
          <div>
            <span class="label">Type</span>
            <span class="code">{{ prop.type }}</span>
          </div>
          <div v-if="prop.expectedParams">
            <span class="label">Expected Parameters</span>
            <span class="code">{{ prop.expectedParams }}</span>
          </div>
          <el-code v-if="prop.example" class="js">
            <code v-html="prop.example"></code>
          </el-code>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import ElCode from './el-code';

export default {
  name: 'SlotDocsItem',
  components: {
    ElCode,
  },
  props: {
    item: {
      type: Object,
    },
  },
};
</script>

<style lang="scss" scoped>
@import '~colors';

.slot-docs-item {
  margin: 35px 0;
}

.meta {
  margin: 6px 0;
}

.name {
  font-size: 17px;
  padding-bottom: 6px;
  border-bottom: 1px solid #ccc;
}

.label {
  margin-right: 6px;
  color: $primary;
  font-weight: bold;

  &.big {
    font-size: 1.1em;
  }
}

.slot-scope {
  display: flex;
  flex-direction: column;

  ul {
    margin-top: 2px;
    margin-left: 6px;
    display: flex;
    flex-direction: column;
  }

  ul li {
    display: flex;
    flex-direction: column;
    margin-bottom: 12px;
  }

  ul li .label {
    color: #868686;
  }
}
</style>
