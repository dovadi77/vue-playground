<template>
  <div class="mb-3">
    <label :for="name" class="form-label">{{ label }}</label>
    <input
      :type="type"
      class="form-control"
      :placeholder="placeholder"
      :value="modelValue"
      :name="name"
      :id="name"
      @input="$emit('update:modelValue', $event.target.value)"
    />
    <small class="text-danger" v-if="errMsg.length > 0">{{ errMsg }}</small>
  </div>
</template>

<script>
export default {
  name: "Input",
  // props: ["name", "id", "type", "errMsg", "modelValue"],
  props: {
    name: String,
    type: String,
    errMsg: String,
    modelValue: String,
    placeholder: String,
    label: String,
  },
  emits: ["update:modelValue"],
};
</script>