<template>
  <material-card
    class="v-card--material-chart"
    v-bind="$attrs"
    v-on="$listeners"
  >
    <template v-slot:heading>
      <apexchart :type="type" height="155" :options="options" :series="data" />
    </template>

    <slot
      slot="reveal-actions"
      name="reveal-actions"
    />

    <slot />

    <slot
      slot="actions"
      name="actions"
    />
  </material-card>
</template>

<script>
  import MaterialCard from "./MaterialCard";
  export default {
    name: 'MaterialChartCard',
    components: {MaterialCard},
    inheritAttrs: false,

    props: {
      data: {
        type: Object,
        default: () => ({}),
      },
      eventHandlers: {
        type: Array,
        default: () => ([]),
      },
      options: {
        type: Object,
        default: () => ({}),
      },
      ratio: {
        type: String,
        default: undefined,
      },
      responsiveOptions: {
        type: Array,
        default: () => ([]),
      },
      type: {
        type: String,
        required: true,
        validator: v => ['bar', 'line', 'pie'].includes(v),
      },
    },
  }
</script>

<style lang="sass">
  .v-card--material-chart
    p
      color: #999

    .v-card--material__heading
      max-height: 185px

      .ct-label
        color: inherit
        opacity: .7
        font-size: 0.975rem
        font-weight: 100

      .ct-grid
        stroke: rgba(255, 255, 255, 0.2)

      .ct-series-a .ct-point,
      .ct-series-a .ct-line,
      .ct-series-a .ct-bar,
      .ct-series-a .ct-slice-donut
          stroke: rgba(255,255,255,.8)

      .ct-series-a .ct-slice-pie,
      .ct-series-a .ct-area
          fill: rgba(255,255,255,.4)
</style>
