<template>
  <h3 class="display-4">Ürün Listesi</h3>
  <div class="row">
    <div class="col-md-8">
      <data-grid :url="url" :columns="columns" keyField="id"></data-grid>
      <pager
        next-text="Sonraki"
        previous-text="Önceki"
        @on-next="next"
        @on-previous="previous"
      ></pager>
    </div>
    <div class="col-md-4"></div>
  </div>
</template>

<script>
import DataGrid from "../components/DataGrid";
import Pager from "../components/Pager";
import axios from "axios";
export default {
  name: "Products",
  components: {
    DataGrid,
    Pager,
  },
  data: () => ({
    pageNumber: 1,
    itemCount: 10,
    columns: [
      {
        name: "id",
        header: "Ürün Kodu",
      },
      {
        name: "name",
        header: "Ürün Adı",
      },
      {
        name: "stock",
        header: "Stok",
      },
      {
        name: "price",
        header: "Fiyat",
      },
      {
        isCommand: true,
        header: "İşlemler",
        name: "select",
        handler: (id) => {
          axios
            .get(process.env.VUE_APP_API_URL + `/api/product/${id}`)
            .then((response) => {
              console.log(response.data);
            });
        },
      },
    ],
  }),
  computed: {
    url: function() {
      return (
        process.env.VUE_APP_API_URL +
        `/api/product/list?page=${this.pageNumber}&count=${this.itemCount}`
      );
    },
  },
  methods: {
    next() {
      this.pageNumber++;
    },
    previous() {
      this.pageNumber--;
    },
  },
};
</script>
