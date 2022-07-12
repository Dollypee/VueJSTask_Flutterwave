<template>
  <section class="join-section">
    <h3>Join our Team of Writers</h3>
    <p>On dasdas, writers earn a living doing what they love. </p>
    <p> Getting started is easy. Just pay a one time <span>$25 fee</span> and everything is ready to go.
    </p>
    <button>JOIN US</button>
  </section>
</template>

<script>
export default {
  name: 'JoinSection',

}
</script>

<style scoped lang="scss">
$--c-black: #2C2C2C;
$--c-black-20:#6E6E6E;
.join-section {
  text-align: center;
  height: 60vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  h3{
    color: $--c-black;
    font-weight: bold;
    font-size: 32px;
    margin: 10px auto;
  }

  p{
    color: $--c-black-20;
    margin: 0 0 10px 0;
    font-size: 22px;

    span{
      font-weight: bolder;
    }
  }

  button{
    color: #fff;
    background: #000000;
    width: 177px;
    margin-top: 20px;
    padding: 10px;
  }

}
</style>