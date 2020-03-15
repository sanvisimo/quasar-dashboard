<template>
  <material-card
    :icon="icon"
    class="v-card--material-stats"
    v-bind="$attrs"
    v-on="$listeners"
  >
    <template v-slot:after-heading>
      <div class="q-ml-auto text-right">
        <div class="text-body2 text-grey text-weight-light" v-text="title" />

        <h3 class="font-weight-light text-primary q-ma-none">
          {{ value }} <small>{{ smallValue }}</small>
        </h3>
      </div>
    </template>

    <q-separator />

    <div class="col-12 flex items-center">
      <q-icon
        :class="colorClass(subIconColor)"
        size="16px"
        class="q-ml-sm q-mr-xs"
        :name="subIcon"
      />

      <span
        :class="colorClass(subTextColor)"
        class="caption grey--text text-weight-light"
        v-text="subText"
      />
    </div>
  </material-card>
</template>

<script>
import MaterialCard from "./MaterialCard";
export default {
  name: "MaterialStatsCard",

  components: {
    MaterialCard
  },

  props: {
    icon: {
      type: String,
      required: true
    },
    subIcon: {
      type: String,
      default: undefined
    },
    subIconColor: {
      type: String,
      default: undefined
    },
    subTextColor: {
      type: String,
      default: undefined
    },
    subText: {
      type: String,
      default: undefined
    },
    title: {
      type: String,
      default: undefined
    },
    value: {
      type: String,
      default: undefined
    },
    smallValue: {
      type: String,
      default: undefined
    }
  },
  methods: {
    colorClass(color) {
      return color ? `text-${subTextColor}` : 'text-grey';
    }
  }
};
</script>

<style lang="sass">
.v-card--material-stats
  display: flex
  flex-wrap: wrap
  position: relative

  > div:first-child
    justify-content: space-between

  .q-card
    border-radius: 4px
    flex: 0 1 auto

  .v-card__text
    display: inline-block
    flex: 1 0 calc(100% - 120px)
    position: absolute
    top: 0
    right: 0
    width: 100%

  .v-card__actions
    flex: 1 0 100%
</style>
