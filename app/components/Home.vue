<template>
  <Page actionBarHidden="true">
    <GridLayout rows="*, auto *, auto">
      <Image
        src="~/assets/foto.jpg"
        iosOverflowSafeArea="true"
        stretch="aspectFill"
        rowSpan="3"
      ></Image>

      <StackLayout row="1" class="text-center p-10 Maincard">
        <Image
          src="~/assets/logo.png"
          stretch="aspectFill"
          class="HortiFrutlogo"
        ></Image>
        <Image
          src="~/assets/campeon.png"
          stretch="aspectFill"
          class="Campeones"
        ></Image>
        <label text="Ingresa tu numero" class="actionLabel" />
        <label text="de empleado" class="actionLabel" margin="0,0,20,0" />
        <TextField v-model="Num" hint="Buscar..." margin="0,0,20,0" />
        <Button
          text="Buscar mis bonos"
          margin="0,0,20,0"
          @tap="buscarMisBonos"
          backgroundColor="#509f4a"
          color="#fff"
        />
      </StackLayout>

      <stackLayout row="2" margin="0,10,0,10">
        <AbsoluteLayout>
          <Button
            text="?"
            class="circular-button"
            @tap="OpenModalImage"
            width="50"
            height="50"
            backgroundColor="#d5012c"
            borderRadius="25"
            color="#fff"
            right="20"
            bottom="20"
          />
        </AbsoluteLayout>
      </stackLayout>
    </GridLayout>
  </Page>
</template>

<script lang="ts">
import ModalError from './ModalError';
import ModalOk from './ModalOk';
import ModalImage from './ModalImage';

import { Http } from '@nativescript/core';

export default {
  methods: {
    logMessage() {
      console.log('You have tapped the message!');
    },
    OpenModalOK(resultsarray) {
      this.$showModal(ModalOk, {
        props: { results: resultsarray, parentModal: this.$modal },
      });
    },
    OpenModalError() {
      this.$showModal(ModalError, {
        props: { parentModal: this.$modal },
      });
    },
    OpenModalImage() {
      this.$showModal(ModalImage, {
        props: { parentModal: this.$modal },
      });
    },
    buscarMisBonos() {
      Http.getJSON(
        'http://api.hortifrut.greenmoonstudios.com/?table=Employees&linkTo=Employee&equalTo=' +
          this.Num
      ).then(
        (result: any) => {
          if (result.status == 200) {
            this.OpenModalOK(result.results);
          } else {
            this.OpenModalError();
          }
        },
        (e) => {
          this.OpenModalError();
        }
      );
    },
  },
  data() {
    return {
      Num: 'ALA000006',
    };
  },
};
</script>

<style></style>
