<template>
  <div class="input">
    <fa class="icon" :icon="icon" :iconColor="iconColor" :style="cssProps" />
    <!-- <input
      :type="type"
      :placeholder="placeholder"
      name="inputData"
      v-model="inputData"
    /> -->
    <input :type="type" :placeholder="placeholder" name="inputData" />
  </div>
</template>

<script>
export default {
  name: "InputField",
  // props: {
  //   placeholder: { type: String, default: "Input" },
  //   type: { type: String, default: "text" },
  //   icon: { type: String, default: "null" },
  //   iconColor: { type: String, default: "black" },
  //   inputData: { type: String, default: "" },
  // },
  props: ["placeholder", "type", "icon", "iconColor", "inputData"],
  computed: {
    cssProps() {
      return {
        "--icon-color": this.iconColor,
      };
    },
  },
  methods: {
    updateData(data) {
      // this.value = data;
      this.$emit("input", data);
      // console.log(data);
    },
  },
};
</script>

<style scoped>
* {
  --icon-color: #00f3b8;
}

.input {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
}

input {
  height: 2rem;
  background: white;
  color: var(--dark-clr);
  border-radius: 2rem;
  padding: 0.2rem 1rem;
  margin: 0.2rem;
  border: none;
  box-shadow: 0 0rem 0rem 0.1rem rgba(0, 0, 0, 0.1);
  font-weight: bold;
  transition: 0.5s;
}

input::placeholder {
  color: var(--mid-dark-clr);
}

input:focus {
  border: none;
  box-shadow: 0 0.1rem 1rem 0.2rem rgba(0, 0, 0, 0.3);
}

.icon {
  /* color: var(--icon-color); */
  color: var(--primary-clr);
  margin: 0 0.5rem;
}
</style>
