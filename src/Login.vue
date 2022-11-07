<template>
  <div class="login-container">
    <!-- <h1>Welcome!</h1> -->
    <div class="blob-container">
      <RandomSVG type="blob" :svgNum="blobID" opacity="0.5" />
    </div>
    <div class="graphic-container">
      <RandomSVG type="graphic" :svgNum="svgID" />
    </div>
    <Form />
    <div class="test_class"></div>
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import RandomSVG from "./components/RandomSVG.vue";

let blobID = Math.floor(Math.random() * 4 + 1);
blobID += "";
// console.log(blobID);

let svgID = Math.floor(Math.random() * 7 + 1);
svgID += "";
// console.log(svgID);

let svgPath;
let svgContent;

fetch("./assets/svg/blobs/blob-" + blobID + ".svg")
  .then((response) => response.text())
  .then((text) => {
    svgPath = text;
    svgContent = svgPath.split(">");
    // console.log(svgContent);
  })
  .then(() => {
    let element = document.getElementsByClassName("test_class")[0];
    element.innerHTML =
      svgContent[0] +
      ">" +
      "<clipPath id='image-mask-" +
      blobID +
      "'>" +
      svgContent[1] +
      ">" +
      "</clipPath>" +
      svgContent[2];
    element.style.width = "100px";
    element.style.height = "100px";
    let imgElement = document.createElement("img");
    imgElement.src = "https://picsum.photos/200";
    imgElement.style.clipPath = "url(#image-mask-" + blobID + ")";
    element.appendChild(imgElement);
  });

export default {
  name: "Login",
  components: { Form, RandomSVG },
  data() {
    return {
      svgID,
      blobID,
    };
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Dosis:wght@200;300;400;500;700;800&display=swap");

* {
  font-family: Dosis, sans-serif;
}

.login-container {
  /* background: chartreuse; */
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.blob-container {
  position: fixed;
  /* background: green; */
  top: -50vh;
  left: -50vw;
  width: 100vw;
  z-index: -2;
}
.graphic-container {
  position: fixed;
  /* background: red; */
  z-index: -1;
}
</style>
