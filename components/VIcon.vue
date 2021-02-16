<template>
    <img 
    :class="className"
    :src="require(`@/media/icons/${name}.svg`)" />
</template>

<script>

export default {
  name: 'VIcon',
    props: {
        name: {
            type: String,
            required: true
        },
    },
    computed: {
        className() {
            return `icon icon_${this.name}`;
        }
    }
}
</script>
<style lang="sass" scoped src="@/media/sass/components/VIcon.sass"></style>
