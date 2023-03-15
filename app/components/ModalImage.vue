<template>
  <Page>
    <StackLayout row="1">
      <Image
        src="https://hortifrut.greenmoonstudios.com/Images/Flayer.jpg"
      ></Image>
      <Button text="Salir" @tap="$modal.close()" class="Okbutton" />
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
