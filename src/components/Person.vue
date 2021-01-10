<template>
  <div class="card p-3">
    <div class="d-flex align-items-center">
      <div class="image">
        <img :src="profilePhoto" class="rounded" width="155" />
      </div>
      <div class="ml-3 w-100">
        <h4 class="mb-0 mt-0">{{ fullname }}</h4>
        <span>{{ personTitle }}</span>
        <div
          class="p-2 mt-2 bg-primary d-flex justify-content-between rounded text-white stats"
        >
          <div class="d-flex flex-column">
            <span class="articles">Makale</span>
            <span class="number1">2</span>
          </div>
          <div class="d-flex flex-column">
            <span class="followers">Takipçi</span>
            <span class="number2">34</span>
          </div>
          <div class="d-flex flex-column">
            <span class="rating">Popülerlik</span>
            <span class="number3"
              >{{ rating }}
              <i class="fas fa-angle-up up" v-if="rating > 5"></i>
              <i class="fas fa-minus neutral" v-if="rating === 5"></i>
              <i class="fas fa-angle-down down" v-if="rating < 5"></i>
            </span>
          </div>
        </div>
        <div class="button mt-2 d-flex flex-row align-items-center">
          <button class="btn btn-sm btn-outline-primary w-100">
            <i class="far fa-envelope"></i> Mesaj At
          </button>
          <button class="btn btn-sm btn-primary w-100 ml-2">
            <i class="fas fa-plus"></i> Takip Et
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "person",
  props: {
    fullname: {
      type: String,
      required: true
    },
    title: {
      type: String
    },
    rating: {
      type: Number,
      default: 3,
      validator: function(value) {
        return value <= 10 && value >= 0;
      }
    },
    photo: {
      type: String
    }
  },
  computed: {
    profilePhoto: function() {
      if (this.photo) {
        return this.photo;
      }
      return "/img/_user.jpg";
    },
    personTitle: function() {
      if (this.title) {
        return this.title;
      }
      return "-";
    }
  }
};
</script>

<style scoped>
.card {
  width: 400px;
  border: none;
  border-radius: 10px;
  background-color: #fff;
}

.stats {
  background: #f2f5f8 !important;
  color: #000 !important;
}

.articles {
  font-size: 10px;
  color: #a1aab9;
}

.number1 {
  font-weight: 500;
}

.followers {
  font-size: 10px;
  color: #a1aab9;
}

.number2 {
  font-weight: 500;
}

.rating {
  font-size: 10px;
  color: #a1aab9;
}

.number3 {
  font-weight: 500;
}
.up {
  color: rgb(34, 121, 39);
}
.neutral {
  color: rgb(199, 196, 31);
}
.down {
  color: rgb(160, 52, 9);
}
</style>
