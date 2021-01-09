<template>
  <div class="row">
    <div class="col-md-3" v-for="p in persons" :key="p.id">
      <person
        :fullname="p.fullname"
        :rating="p.rating"
        :title="p.title"
        :photo="p.photo"
      />
    </div>
  </div>
  <div class="row mt-5">
    <div class="col-md-12">
      <div class="card">
        <div class="card-header">
          Özet
        </div>
        <div class="card-body">
          <h5 class="card-title">İçerik fırsatları</h5>
          <p class="card-text">
            İnsan kaynakları safasında içerik araması yapabilirsiniz.
          </p>
          <custom-button>
            İncele
          </custom-button>
          <custom-button variant="primary">
            Önceki
            <template #before-icon>
              <i class="fas fa-angle-left"></i>
            </template>
          </custom-button>
          <custom-button variant="warning">
            <template #after-icon>
              <i class="fas fa-angle-right"></i>
            </template>
            <b>Sonraki</b>
          </custom-button>
          <basic-button variant="success" font="fas fa-save">
            Kaydet
          </basic-button>
          <basic-button variant="danger">
            İptal
          </basic-button>
          <button class="btn btn-primary" @click="openModal">Modal Aç</button>
        </div>
        <div class="modal" tabindex="-1">
          <div class="modal-dialog">
            <div class="modal-content">
              <div class="modal-header">
                <h5 class="modal-title">Modal title</h5>
                <button
                  type="button"
                  class="close"
                  data-dismiss="modal"
                  aria-label="Close"
                >
                  <span aria-hidden="true">&times;</span>
                </button>
              </div>
              <div class="modal-body">
                <p>Modal body text goes here.</p>
              </div>
              <div class="modal-footer">
                <button
                  type="button"
                  class="btn btn-secondary"
                  data-dismiss="modal"
                >
                  Close
                </button>
                <button type="button" class="btn btn-primary">
                  Save changes
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Person from "./components/Person";
import CustomButton from "./components/CustomButton";
import BasicButton from "./components/BasicButton";
import jsonData from "./data.json";
export default {
  name: "App",
  components: {
    Person,
    CustomButton,
    BasicButton,
  },
  data: () => ({
    persons: [],
  }),
  mounted() {
    this.persons = jsonData;
  },
  methods: {
    openModal() {
      window.$(".modal").modal("show");
    },
  },
};
</script>

<style>
#app {
  font-family: Segoe UI;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
