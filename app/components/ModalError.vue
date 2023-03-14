<template>
  <Page>
    <StackLayout row="1" class="text-center p-5">
      <label text="¡Lo sentimos!" class="actionLabelError" />
      <label text="No hemos encontrado" class="actionLabelErrorSub" />
      <label text="tu numero de empleado" class="actionLabelErrorSub" />
      <Button text="Salir" @tap="$modal.close()" />
    </StackLayout>
  </Page>
</template>

<script>
export default {
  props: ['parentModal'],
};
</script>
