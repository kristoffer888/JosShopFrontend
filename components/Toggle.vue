<template>
  <div class="toggle-wrapper">
    <label class="toggle">
      <input type="checkbox" :checked="(mode === 'dark') ? 'checked' : false">
      <span class="toggler round"></span>
    </label>
  </div>
</template>

<script>
</script>

<style>
.toggle{
  position: relative;
  display: inline-block;
  width: 60px;
  height: 34px;
}

.toggle input{
  opacity: 0;
  width: 0;
  height: 0;
}

.toggler{
  position: absolute;
  cursor: pointer;
  top: 0;
  right: 0;
  bottom: 0;
  background: #152028;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}
.toggler:before{
  position: absolute;
  content: "";
  height: 26px;
  width: 26px;
  left: 4px;
  bottom: 4px;
  background: #FFF;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

</style>
