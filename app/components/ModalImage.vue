<template>
  <Page>
    <StackLayout row="1">
      <Image
        src="http://hortifrut.greenmoonstudios.com/Images/Flayer.jpg"
      ></Image>
      <Button text="Salir" @tap="$modal.close()" />
    </StackLayout>
  </Page>
</template>

<script lang="ts">
import Vue from 'nativescript-vue';
export default Vue.extend({
  props: ['Num', 'parentModal'],
  data() {
    return {
      isImageLoaded: true,
    };
  },
  methods: {},
});
</script>
