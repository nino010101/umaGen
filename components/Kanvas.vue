<template>
  <div class="canvas-container">
    <v-stage :config="configKonva">
      <v-layer>
        <v-image
          :config="{
            image: image,
          }"
        />
        <v-image
          :config="{
            image: iconImage,
            x: 36,
            y: 85,
          }"
        />
        <v-text :config="name" />
        <v-text :config="title" />
        <v-text :config="body" />
      </v-layer>
    </v-stage>
  </div>
</template>

<script>
export default {
  props: {
    nameText: {
      type: String,
      required: true,
    },
    bodyText: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      image: null,
      iconImage: null,
      name: {
        text: this.nameText,
        fontFamily: 'Wanpaku',
        fontSize: 27,
        fill: '#ffffff',
        x: 20,
        y: 27,
      },
      title: {
        text: this.titleText,
        fontFamily: 'Wanpaku',
        fontSize: 36,
        fill: '#753424',
        x: 220,
        y: 102,
      },
      body: {
        text: this.bodyText,
        fontFamily: 'Wanpaku',
        fontSize: 32,
        fill: '#753424',
        x: 220,
        y: 168,
      },
      configKonva: {
        width: 1000,
        height: 300,
      },
    }
  },
  watch: {
    nameText() {
      this.name.text = this.nameText
      this.title.text = this.nameText + 'のヒミツ'
    },
    bodyText() {
      this.body.text = this.bodyText
    },
    icon() {
      const image = new Image()
      image.src = this.icon
      image.onload = () => {
        // set image only when it is loaded
        this.iconImage = image
      }
    },
  },
  created() {
    const image = new Image()
    image.src = './image/base.png'
    image.onload = () => {
      // set image only when it is loaded
      this.image = image
    }
  },
}
</script>
<style lang="scss">
.canvas-container {
  border: solid 1px #ccc;
  margin: 12px 0px;
}
</style>
