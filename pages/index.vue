<template>
  <section class="container">
    <div id="cube">
      <div class="front"></div>
      <div class="back"></div>
      <div class="right"></div>
      <div class="left"></div>
      <div class="top"></div>
      <div class="bottom"></div>
    </div>
  </section>
</template>

<script>
export default {
  mounted() {
    var lastMouseX = 0,
      lastMouseY = 0;
    var rotX = 0,
      rotY = 0;

    document.addEventListener("mousedown", function abc(ev) {
      console.log("__");
      lastMouseX = ev.clientX;
      lastMouseY = ev.clientY;
      document.addEventListener("mousemove", mouseMoved);
    });

    document.addEventListener("mouseup", function () {
      document.removeEventListener("mousemove", mouseMoved);
    });

    function mouseMoved(ev) {
      console.log("hi");
      const speed = 0.5;
      var deltaX = ev.pageX - lastMouseX;
      var deltaY = ev.pageY - lastMouseY;

      lastMouseX = ev.pageX;
      lastMouseY = ev.pageY;

      rotY -= deltaX * speed;
      rotX += deltaY * speed;

      document.querySelector("#cube").style.transform =
        "translateZ( -100px) rotateX( " +
        rotX +
        "deg) rotateY(" +
        rotY +
        "deg)";
    }
  },
};
</script>

<style>
.container {
  margin: auto;
  width: 200px;
  height: 200px;
  position: relative;
  perspective: 1000px;
  margin-top: 300px;
  cursor: pointer;
}

#cube {
  width: 100%;
  height: 100%;
  position: absolute;
  transform-style: preserve-3d;
}

#cube div {
  margin: 0;
  width: 196px;
  height: 196px;
  display: block;
  position: absolute;
  border: 2px solid black;
  opacity: 0.5;
}

#cube .front {
  transform: rotateY(0deg) translateZ(100px);
  background-color: red;
}

#cube .back {
  transform: rotateX(180deg) translateZ(100px);
  background-color: blue;
}

#cube .right {
  transform: rotateY(90deg) translateZ(100px);
  background-color: green;
}

#cube .left {
  transform: rotateY(-90deg) translateZ(100px);
  background-color: yellow;
}

#cube .top {
  transform: rotateX(90deg) translateZ(100px);
  background-color: orange;
}

#cube .bottom {
  transform: rotateX(-90deg) translateZ(100px);
  background-color: purple;
}
</style>
