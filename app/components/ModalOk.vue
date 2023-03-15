<template>
  <Page>
    <GridLayout rows="auto, *, auto ">
      <StackLayout row="0" class="text-center p-2">
        <Label text="¡Conoce tus Bonos!" class="text-center ModalTitlelabel" />
        <Label text="Acumulado total:" class="text-center ModalTitlelabelSub" />
        <Label
          :text="'$' + parseFloat(total).toFixed(2)"
          class="text-center ModalTitleAmountlabelSub"
        />
      </StackLayout>
      <StackLayout row="1" class="text-center p-2">
        <ScrollView orientation="vertical">
          <GridLayout :rows="rows">
            <StackLayout
              v-for="(item, index) in results"
              :key="index"
              :row="index"
            >
              <Label
                col="0"
                :text="item.Descr + ': '"
                class="text-center LabelDesc"
              />
              <Label
                col="1"
                :text="'$' + parseFloat(item.Amount).toFixed(2)"
                class="text-center LabelAmount"
              />
            </StackLayout>
          </GridLayout>
        </ScrollView>
      </StackLayout>
      <StackLayout row="2" class="text-center p-2">
        <Button text="Salir" @tap="$modal.close()" class="Okbutton" />
      </StackLayout>
    </GridLayout>
  </Page>
</template>

<script lang="ts">
import Vue from 'nativescript-vue';
export default Vue.extend({
  props: ['results', 'parentModal'],
  data() {
    return {
      total: 0,
      rows: '',
    };
  },
  mounted() {
    for (var i = 0; i < this.results.length; i++) {
      this.rows = this.rows + '*,';
      this.total += parseFloat(this.results[i].Amount);
    }
  },
});
</script>
