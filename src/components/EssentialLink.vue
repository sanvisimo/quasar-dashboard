<template>
  <q-item
    clickable
    tag="a"
    exact
    class="q-my-sm"
    exact-active-class="q-item__active"
    :to="link"
  >
    <q-item-section v-if="icon" avatar>
      <q-icon :name="icon" />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{ title }}</q-item-label>
      <q-item-label caption>
        {{ caption }}
      </q-item-label>
    </q-item-section>
  </q-item>
</template>

<script>
export default {
  name: "EssentialLink",
  props: {
    title: {
      type: String,
      required: true
    },

    caption: {
      type: String,
      default: ""
    },

    link: {
      type: String,
      default: "#"
    },

    icon: {
      type: String,
      default: ""
    }
  }
};
</script>

<style lang="sass" scoped>
.q-item__active
  background-color: $primary
  color: #fff
  border-radius: $generic-border-radius
</style>
