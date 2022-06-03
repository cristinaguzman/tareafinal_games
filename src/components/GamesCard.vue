<template>
  <div>
    <div class="container texto col-sm-12">
      <div class="row table-secondary row row-cols-1 row-cols-sm-2 row-cols-md-4">
        <div
          class="card col-12 col-sm-6 col-md-4"
          v-for="(AllGame, $index) of AllGames"
          :key="$index"
        >
          <img :src="AllGame.background_image" class="card-img-top" alt="..." />
          <div class="card-body bg-secondary">
            <h5 class="card-title bg-light">{{ AllGame.name }}</h5>
            <ul class="list-group list-group-flush">
              <li class="list-group-item">Rating: {{ AllGame.rating }}</li>
              <li class="list-group-item">Released: {{ AllGame.released }}</li>
              <li class="list-group-item">Updated: {{ AllGame.updated }}</li>
            </ul>
            <button type="button" class="btn btn-success" @click="showModal = true">Opinar</button>
          </div>
        </div>
      </div>
    </div>
    <!--Component-->
    <modal-op :show="showModal" @close="showModal = false"> </modal-op>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import { mapActions } from 'vuex'
import ModalOp from './ModalOp.vue'

export default {
  components: {
    ModalOp,
  },
  props: {
    categoria: { type: String, default: 'desconocida' },
  },
  data() {
    return {
      showModal: false,
      addOpinion: '',
    }
  },
  computed: {
    ...mapState('GamesModule', {
      AllGames: (state) => state.games,
    }),
    ...mapState('GamesModule', ['opinions']),
    AllCategory() {
      if (this.categoria === 'opinions') {
        return this.$store.getters['GamesModule/opinionGame']
      } else {
        return this.$store.getters['GamesModule/adminGames']
      }
    },
  },
  methods: {
    ...mapActions('GamesModule', ['newOpinions', 'openModal']),
    manejarClick() {
      this.newOpinions({
        nombre: this.addOpinion,
        categoria: this.categoria,
      })
      this.addOpinion = ''
    },
  },
}
</script>

<style>
.texto {
  font-family: 'Courier New', Courier, monospace;
  font-size: 15px;
}
</style>
