<template>
  <div
      class="h-text-field"
      :class="classes"
  >
    <div class="h-text-field__wrapper">
      <input
          ref="input"
          type="text"
          class="h-text-field__input"
          :value="value"
          @input="e => input(e.target.value)"
          @change="e => change(e.target.value)"
          @focus="onFocus"
          @blur="onBlur"
      >
    </div>
  </div>
</template>

<script lang="ts">
import {Component, Vue, Prop} from "vue-property-decorator";
import {Classes} from "@/components/h-text-fields/IHTextField";

@Component({})
export default class HTextField extends Vue {
  @Prop({
    type: [String, Number],
    default: '',
  })
  public value: string | number;

  private input(value: string | number): void {
    this.$emit('input', value);
  }

  private change(value: string | number): void {
    this.$emit('change', value);
  }

  private isFocused = false;

  private onFocus(): void {
    this.isFocused = true;
  }

  private onBlur(): void {
    this.isFocused = false;
  }

  private get isDirty(): boolean {
    return !!String(this.value);
  }

  private get classes(): Classes {
    return {
      'h-text-field--is-focus': !!this.isFocused,
      'h-text-field--is-dirty': !!this.isDirty,
    }
  }
}
</script>