<template>
  <q-card v-bind="$attrs" :class="classes" class="v-card--material q-pa-sm">
    <div class="flex col-grow">
      <q-avatar
        v-if="avatar"
        size="128px"
        class="mx-auto v-card--material__avatar elevation-6"
        color="grey"
      >
        <q-img :src="avatar" />
      </q-avatar>

      <div
        v-else
        :class="[
          {
            'q-pa-lg': !$slots.image
          },
          `bg-${color}`
        ]"
        style="margin-bottom: -6px;"
        :style="{
          'max-height': icon ? '90px' : undefined,
          width: icon ? 'auto' : '100%'
        }"
        class="text-start v-card--material__heading shadow-6"
      >
        <slot v-if="$slots.heading" name="heading" />

        <slot v-else-if="$slots.image" name="image" />

        <div
          v-else-if="title && !icon"
          class="text-h6 text-weight-light"
          v-text="title"
        />

        <q-icon v-else-if="icon" size="32px" :name="icon" />

        <div v-if="text" class="headline text-weight-thin" v-text="text" />
      </div>

      <div v-if="$slots['after-heading']" class="q-ml-md">
        <slot name="after-heading" />
      </div>

      <div v-else-if="icon && title" class="q-ml-sm">
        <div class="card-title text-weight-light" v-text="title" />
      </div>
    </div>

    <slot />

    <template v-if="$slots.actions">
      <q-separator class="q-mt-sm" />

      <q-card-actions class="q-pb-none">
        <slot name="actions" />
      </q-card-actions>
    </template>
  </q-card>
</template>

<script>
export default {
  name: "MaterialCard",

  props: {
    avatar: {
      type: String,
      default: ""
    },
    color: {
      type: String,
      default: "positive"
    },
    icon: {
      type: String,
      default: undefined
    },
    image: {
      type: Boolean,
      default: false
    },
    text: {
      type: String,
      default: ""
    },
    title: {
      type: String,
      default: ""
    }
  },

  computed: {
    classes() {
      return {
        "v-card--material--has-heading": this.hasHeading
      };
    },
    hasHeading() {
      return Boolean(this.$slots.heading || this.title || this.icon);
    },
    hasAltHeading() {
      return Boolean(this.$slots.heading || (this.title && this.icon));
    }
  }
};
</script>

<style lang="sass">
.v-card--material
  .v-card--material__heading
    border-radius: $generic-border-radius

  &__avatar
    position: relative
    top: -64px
    margin-bottom: -32px

  &__heading
    position: relative
    top: -25px
    transition: .3s ease
    z-index: 1
</style>
