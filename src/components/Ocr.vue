<template>
   <div id="ocr">
    <b-form-file 
      v-model="form.file"
      :state="Boolean(form.file)"
      placeholder="Elija un archivo o arrastrelo hasta aquí..."
      drop-placeholder="Suelte aqui su archivo..."
      name="foto"
      ref="file-input"
      accept=".pdf, .gif, .png, .jpg, .jpeg, .tif, .tiff, .bmp"
    ></b-form-file>
    <b-button @click="getOcr" class="mt-2">Subir factura</b-button>  
     <p class="mt-2">{{error}}</p>
  <b-card-group  v-for="factura in facturas" :key="factura.id">
   <b-card class="mt-3" header="Datos de factura ">
      <pre class="m-0">{{ factura.data }}</pre>
    </b-card>
  </b-card-group>
 </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
      return {
          form:{
              food: 'eng',
              file: null,
              filetype: 'jpg',
              apikey: '9fc6283ca788957'
          },
          facturas: [],
          error: '',
          id: 0,
        show: true
      }
    },
    methods: {
        getOcr(){  
          this.error= 'Loading...'
            const fd= new FormData();
            fd.append('file', this.form.file);
            fd.append('apikey',this.form.apikey)
          axios.post('https://api.ocr.space/parse/image',fd
            )
            .then(res=>{
              this.error= ''
               this.facturas.push({
               'id': this.id,
                'data': res.data.ParsedResults[0].ParsedText
                })
                this.id++
             })
            .catch(e =>{
              console.log(e)
              this.error = 'Algo salio mal, intenta de nuevo mas tarde.'

            })
        }
    }
  }
</script>

<style >
.custom-file-input:lang(en) ~ .custom-file-label::after {
  content: 'Seleccionar';
}
#ocr{
  max-width: 600px; 
  margin: auto; 
  flex-direction: column;
  align-content: center;
}
</style>