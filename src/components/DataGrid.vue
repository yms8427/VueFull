<template>
  <table class="table table-hover table-stripped">
    <thead>
      <tr>
        <th v-for="h in columns" :key="h.name">{{ h.header }}</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="r in rows" :key="r[keyField]">
        <td v-for="h in dataColumns" :key="h.name">{{ r[h.name] }}</td>
        <td v-for="h in actionColumns" :key="h.name">
          <button
            class="btn btn-sm btn-primary"
            @click="h.handler(r[keyField])"
          >
            <i class="fas fa-mouse-pointer"></i> Seç
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>
<script>
import axios from "axios";
export default {
  name: "DataGrid",
  props: {
    columns: {
      type: Array,
    },
    url: {
      type: String,
      required: true,
    },
    keyField: {
      type: String,
      required: true,
    },
  },
  data: () => ({
    rows: [],
  }),
  mounted() {
    this.load();
  },
  computed: {
    dataColumns: function() {
      return this.columns.filter((c) => !c.isCommand);
    },
    actionColumns: function() {
      return this.columns.filter((c) => c.isCommand);
    },
  },
  methods: {
    load() {
      axios.get(this.url).then((response) => {
        this.rows = response.data;
      });
    },
  },
  watch: {
    url: function() {
      this.load();
    },
  },
};
</script>
