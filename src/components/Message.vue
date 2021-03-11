<template>
  <div class="box">
    <p>
      <slot></slot>
    </p>
    <small>PS: Basic calculations only</small>
  </div>
</template>

<script>

export default {
  name: 'Message',
}
</script>

<style>
  .box {
    text-align: center;
    margin: 1px auto;
    margin-bottom: 20px;
    max-width: 350px;
    font-family: 'Akaya Telivigala', cursive;
  }
  .box p {
    margin: 0px;
    font-size: 28px;
    text-transform: capitalize;
  }

</style>