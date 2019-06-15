<template>
  <div id="translateForm" class="row">
      <div class="col-md-6 offset-md-3">
        <form  @submit.prevent="formSubmit">
          <div class="form-group">
            <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a word">
          </div>
          <div class="form-group">
            <select class="form-control"  v-model="language">
              <option value="ru">Russian</option>
              <option value="es">Spanish</option>
              <option value="fr">French</option>
              <option value="zh">Chinese</option>
              <option selected value="de">German</option>
            </select>
          </div>
          <div class="form-group">
            <input class="btn btn-outline-success" type="submit" value="Translate">
          </div>
        </form>
      </div><!-- end col -->
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data(){
    return {
      textToTranslate: '',
      language: 'de',
    }
  },
  methods: {
    formSubmit(){
      this.$emit('formSubmit',this.textToTranslate,this.language);
    }
  }
}
</script>

<style>

</style>
