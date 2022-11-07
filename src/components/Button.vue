<template>
  <button :type="type">
    <p class="button-txt">{{ text }}</p>
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: {
      type: String,
      default: "Button",
    },
    type: {
      type: String,
      default: "",
    },
  },
};
</script>

<style scoped>
button {
  border: none;
  background: var(--primary-clr);
  height: 2.4rem;
  border-radius: 3rem;
  box-shadow: 0 0.1rem 1rem 0.2rem rgba(126, 126, 126, 0.3);
  cursor: pointer;
  width: max-content;
  position: relative;
  overflow: hidden;
  transition: 0.5s;
}

button::before {
  content: "";
  position: absolute;
  width: 0;
  aspect-ratio: 1;
  border-radius: 50%;
  top: 50%;
  left: 50%;
  background: var(--light-clr);
  opacity: 0.2;
  transition: 0.5s ease;
}

button:hover,
button:focus {
  box-shadow: 0 0.1rem 1rem 0.2rem rgba(0, 0, 0, 0.3);
}

button:hover::before,
button:focus::before {
  width: 110%;
  left: -5%;
  top: -55%;
}

.button-txt {
  color: white;
  font-size: 1rem;
  font-weight: bold;
  padding: 0rem 1.5rem;
}
</style>
