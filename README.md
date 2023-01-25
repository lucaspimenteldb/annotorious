## MVC
Para usar a tradução para o português:
Clonar este projeto junto do recogito-core-mvc(https://github.com/lucaspimenteldb/recogito-core-mvc) na mesma pasta

`cd recogito-core-mvc` <br>
`npm install` <br>
`npm link` <br>
`cd ..` voltar à pasta raíz dos dois projetos 

`cd annotorious-mvc` <br>
`npm install` <br>
`npm link @recogito/recogito-client-core`

## Using it with vue

```html
<template>
  <div>
    <div class="container">
      <img src="@/assets/redacao-model-1.jpg" ref="redacao" alt="" />
    </div>
  </div>
</template>
<script>
import { Annotorious } from "@recogito/annotorious";
import "@recogito/annotorious/dist/annotorious.min.css";
export default {
  name: "MarkerTests",
  data() {
    return {
      anno: null,
      isStudent: false,
    };
  },
  methods: {
    initAnno() {
      this.anno = new Annotorious({
        image: this.$refs.redacao,
        widgets: [
          "COMMENT",
          {
            widget: "TAG",
            vocabulary: [
              "Ortografia",
              "Sintaxe",
              "Sentido",
              "Pontuação",
              "Tema",
              "Respeito",
            ],
          },
        ],
      });

      // this.anno.on("createAnnotation", function (annotation) {
      // });

      // this.anno.on("createSelection", function (selection) {
      // });

      // this.anno.on("deleteAnnotation", function (selection) {
      // });

      // this.anno.on("mouseEnterAnnotation", function (annotation, ) {
      // });

      // this.anno.on("selectAnnotation", function (annotation, ) {
      // });

      // this.anno.on("cancelSelected", function () {
      // });

      // this.anno.on("clickAnnotation", function (annotation) {
      // });
    },
  },
  mounted() {
    this.initAnno();

    //  se o aluno for estudante permitir apenas ver as anotações
    this.anno.readOnly = this.isStudent;

    // salvar o corretor que está avaliando a redação
    this.anno.setAuthInfo({ id: "asdfasdfasd", displayName: "Corretor x" });
  },
};
</script>

<style scoped>
.container {
  max-width: 100vw;
  max-height: 100vh;
  display: flex;
}
img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

/** borda externa da caixinha **/
>>> svg.a9s-annotationlayer .a9s-annotation .a9s-outer,
>>> svg.a9s-annotationlayer .a9s-selection .a9s-outer {
  display: none;
}

/** borda interna da caixinha **/
>>> svg.a9s-annotationlayer .a9s-selection .a9s-inner,
>>> svg.a9s-annotationlayer .a9s-annotation .a9s-inner {
  stroke: none;
  fill: rgba(255, 202, 29, 0.5);
}

/** efeito de hover das caixinhas criadas **/
>>> svg.a9s-annotationlayer .a9s-annotation:hover .a9s-inner {
  fill: rgba(214, 167, 12, 0.2);
}

/** bolinhas externas das bordas **/
>>> svg.a9s-annotationlayer .a9s-handle .a9s-handle-outer {
  fill: #ddd;
  stroke: #ddd;
  transform: scale(0.7);
}
/* bolinhas internas das bordas */
>>> svg.a9s-annotationlayer .a9s-handle .a9s-handle-inner {
  fill: #222;
  stroke: #222;
  transform: scale(0.5);
}

/* desabilitar a caixinha de respostas */
>>> .r6o-editor .r6o-widget.comment + .r6o-widget.comment.editable {
  display: none;
}
</style>
```
