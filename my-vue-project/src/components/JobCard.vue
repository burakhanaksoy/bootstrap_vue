<template>
  <b-col col lg="4" class="my-5"
    ><div>
      <b-card
        :title="name"
        img-src="https://picsum.photos/600/300/?image=25"
        img-alt="Image"
        img-top
        tag="article"
        style="max-width: 20rem"
      >
        <b-card-text>
          Some quick example text to build on the card title and make up the
          bulk of the card's content.
        </b-card-text>

        <b-button href="#" variant="primary">Apply</b-button>
      </b-card>
    </div></b-col
  >
</template>

<script>
export default {
  props: ["name"],
};
</script>

<style lang="scss" scoped>
</style>