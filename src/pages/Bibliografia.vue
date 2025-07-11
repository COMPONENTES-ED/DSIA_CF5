<template>
  <div class="curso-main-container referencias">
    <BannerInterno
      icono="fas fa-book"
      titulo="Referencias bibliográficas"
    ></BannerInterno>
    <div class="container tarjeta tarjeta--blanca p-4 p-md-5 mb-5">
      <div v-for="ref in orderedData" :key="ref.link" class="referencias__item">
        <span v-html="ref.referencia"></span
        ><a v-if="ref.link" class="ms-1" :href="ref.link" target="_blank"
          ><span v-html="ref.link"></span
          ><i class="ms-1 fas fa-external-link-alt"></i
        ></a>
        <hr class="my-3" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Referencias',
  data: () => ({
    referencias: [
      {
        referencia:
          'Bergström, G., Hujainah, F., Ho-Quang, T., Jolak, R., Rukmono, S. A., Nurwidyantoro, A., & Chaudron, M. R. V. (2022). Evaluating the layout quality of UML class diagrams using machine learning. Journal of Systems and Software, 192.',
        link: 'https://doi.org/10.1016/j.jss.2022.111413',
      },
      {
        referencia:
          'Blanco, P., & Sánchez, J. (2023). Fundamentos de la programación orientada a objetos con Java. Ra-Ma Editorial.',
        link: '',
      },
      {
        referencia:
          'Deitel, P., & Deitel, H. (2024). Java How to Program (12th ed.). Pearson Education.',
        link: '',
      },
      {
        referencia:
          'Freeman, E., Robson, E., Sierra, K., & Bates, B. (2021). Head First Design Patterns (2nd ed.). O"Reilly Media.',
        link:
          'https://archive.org/details/head-first-design-patterns-eric-freeman-elisabeth-robson-bert-bates-etc.-z-lib.org',
      },
      {
        referencia:
          'Gamma, E., Helm, R., Johnson, R., & Vlissides, J. (2023). Design Patterns: Elements of Reusable Object-Oriented Software (Anniversary ed.). Addison-Wesley Professional.',
        link: '',
      },
      {
        referencia:
          'García, A., & Martínez, C. (2023). UML: Modelado de software para profesionales. Alfaomega.',
        link: '',
      },
      {
        referencia:
          'Larman, C. (2022). Applying UML and Patterns: An Introduction to Object-Oriented Analysis and Design (4th ed.). Pearson Education.',
        link: '',
      },
      {
        referencia:
          'López, J. M., & Montero, F. (2024). Patrones de diseño en Java: Una guía práctica. Universidad de Castilla-La Mancha.',
        link: '',
      },
      {
        referencia:
          'Martin, R. C. (2017). Clean Architecture: A Craftsman’s Guide to Software Structure and Design. Prentice Hall.',
        link:
          'https://agorism.dev/book/software-architecture/%28Robert%20C.%20Martin%20Series%29%20Robert%20C.%20Martin%20-%20Clean%20Architecture_%20A%20Craftsman%E2%80%99s%20Guide%20to%20Software%20Structure%20and%20Design-Prentice%20Hall%20%282017%29.pdf',
      },
      {
        referencia:
          'Martin, R. C. (2021). Agile Software Development, Principles, Patterns, and Practices (2nd ed.). Pearson Education.',
        link: '',
      },
      {
        referencia:
          'Phillips, D. (2024). Python 3 Object-Oriented Programming (4th ed.). Packt Publishing.',
        link: '',
      },
      {
        referencia:
          'Sánchez, G. (2022). Programación orientada a objetos: Un enfoque práctico. Universidad Nacional Autónoma de México.',
        link: '',
      },
      {
        referencia:
          'Sweigart, A. (2019). Automate the Boring Stuff with Python: Practical Programming for Total Beginners (2nd ed.). No Starch Press.',
        link: 'https://archive.org/details/Automate-Boring-Stuff-Python-2nd',
      },
      {
        referencia:
          'Valdés-Miranda, C., & Rodríguez, P. (2024). Diseño y programación orientada a objetos: Una perspectiva práctica. Anaya Multimedia.',
        link: '',
      },
      {
        referencia:
          'Vo, M. H. L., & Hoang, Q. (2020). Transformation of uml class diagram into owl ontology. Journal of Information and Telecommunication, 4(1), 1–16.',
        link: 'https://doi.org/10.1080/24751839.2019.1686681',
      },
      {
        referencia:
          'Yusuf, O. (2023). DEVELOPMENT OF A LEARNING MANAGEMENT SYSTEM FOR PHYTON PROGRAMMING LANGUAGE. Caleb International Journal of Development Studies, 06(02), 164–179.',
        link:
          'https://www.cijds.calebuniversity.edu.ng/public_html/files/published_paper/volume-6/issue-2/L2EQL77L.pdf',
      },
    ],
  }),
  computed: {
    orderedData() {
      return [...this.referencias].sort((a, b) => {
        const afl = this.quitarAcentos(a.referencia.split(' ')[0].toLowerCase())
        const bfl = this.quitarAcentos(b.referencia.split(' ')[0].toLowerCase())
        if (afl < bfl) return -1
        if (afl > bfl) return 1
        return 0
      })
    },
  },
  methods: {
    quitarAcentos(str) {
      return str.normalize('NFD').replace(/[\u0300-\u036f]/g, '')
    },
  },
}
</script>

<style lang="sass">
.referencias
  &__item
    &:last-child
      hr
        display: none
    a
      color: $blue
      text-decoration: underline
      overflow-wrap: break-word
</style>
