<template>
  <div id="app">
    <h-text-field
        v-model="textField"
    ></h-text-field>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

import HTextField from "@/components/h-text-fields/HTextField.vue";


@Component({
  components: {
    HTextField,
  }
})
export default class App extends Vue {
  private textField: string | number = '';
  private inputTextField(value: string | number): void {
    this.textField = value;
  }
}
</script>