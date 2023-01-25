## MVC
Para usar a tradução para o português:
Clonar este projeto junto do recogito-core-mvc(https://github.com/lucaspimenteldb/recogito-core-mvc) na mesma página

`cd recogito-core-mvc` <br>
`npm install` <br>
`npm link` <br>
`cd ..` voltar à pasta raíz dos dois projetos 

`cd annotorious-mvc` <br>
`npm install` <br>
`npm link @recogito/recogito-client-core`

## Using it with vue

Below is a minimal example for using Annotorious in Vue.js. Thanks to 
[Grant Brits](https://github.com/gbrits) for this contribution!

```html
<template>
  <div>
    <img id="plan" src="img.png" style="width: 100%; max-width: 1024px;" />
  </div>
</template>

<script>
  import { Annotorious} from '@recogito/annotorious';
  import '@recogito/annotorious/dist/annotorious.min.css';

  export default {
    
    data() {
      return {
        anno: null
      }
    },

    methods: {
      initAnno() {
        this.anno = new Annotorious({
          image: document.getElementById("plan")
        });

        this.anno.on('createAnnotation', function (annotation) {
          console.log('Created annotation', annotation);
        });

        this.anno.on('createSelection', function (selection) {
          console.log('Created selection', selection);
        });

        this.anno.on('deleteAnnotation', function (annotation) {
          console.log('Delete annotation', selection);
        });

        this.anno.on('mouseEnterAnnotation', function (annotation, element) {
          console.log('Mouse ENTERED annotation', annotation);
        });

        this.anno.on('selectAnnotation', function (annotation, element) {
          console.log('Select annotation', annotation);
        });

        this.anno.on('cancelSelected', function (selection) {
          console.log('UNSELECTED');
        });

        this.anno.on('clickAnnotation', function (annotation, element) {
          console.log('Clicked annotation', annotation);
        });
      }
    },

    mounted() {
      this.initAnno();
    }
  }
</script>
```
