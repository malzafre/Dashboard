<template>
  <v-container class="d-flex justify-center align-center" fluid style="padding: 0 25px 20px 25px;">
    <v-row align="center" justify="left">
      <v-col cols="12">
        <v-text-field v-model="searchQuery" label="Search" prepend-inner-icon="mdi-magnify" variant="outlined"
          hide-details single-line @input="search"></v-text-field>
      </v-col>
      <v-col v-for="(card, index) in filteredCards" :key="index" cols="6" md="3" sm="4" lg="3">
        <v-card class="mx-auto" link="" to="/profile">
          <v-container
            :style="{ height: '250px', backgroundImage: 'url(' + card.image + ')', backgroundSize: 'cover', backgroundRepeat: 'repeat' }"></v-container>

          <v-card-title style="font-weight: 900;">{{ card.title }}</v-card-title>

          <v-card-text>
            {{ card.address }}
          </v-card-text>
        </v-card>
      </v-col>
      <v-btn class="add-card-btn" fab dark color="primary" @click="openDialog">
        <v-icon dark>mdi-plus</v-icon>
      </v-btn>
      <v-dialog v-model="dialog" max-width="800px">
        <v-card>
          <v-card-actions>
            <AddAccommodation />
          </v-card-actions>
        </v-card>
      </v-dialog>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: '',
      cards: [
        {
          title: 'Kim Angela Homestay',
          address: 'Paniman, Caramoan, Camarines Sur',
          image: '/1.jpg'
        },
        {
          title: 'HAHAHA',
          address: 'Paniman, Caramoan, Camarines Sur',
          image: '/1.jpg'
        },
        {
          title: 'Kim Angela Homestay',
          address: 'Paniman, Caramoan, Camarines Sur',
          image: '/1.jpg'
        },
        {
          title: 'Kim Angela Homestay',
          address: 'Paniman, Caramoan, Camarines Sur',
          image: '/1.jpg'
        },
        {
          title: 'Kim Angela Homestay',
          address: 'Paniman, Caramoan, Camarines Sur',
          image: '/1.jpg'
        },
        {
          title: 'Kim Angela Homestay',
          address: 'Paniman, Caramoan, Camarines Sur',
          image: '/1.jpg'
        },
        {
          title: 'Kim Angela Homestay',
          address: 'Paniman, Caramoan, Camarines Sur',
          image: '/1.jpg'
        },
        {
          title: 'Kim Angela Homestay',
          address: 'Paniman, Caramoan, Camarines Sur',
          image: '/1.jpg'
        },

      ],
      filteredCards: [],
      dialog: false // Initially dialog is closed
    }
  },
  created() {
    this.filteredCards = this.cards;
  },
  methods: {
    search() {
      if (this.searchQuery.trim() === '') {
        this.filteredCards = this.cards;
      } else {
        this.filteredCards = this.cards.filter(card => {
          return card.title.toLowerCase().includes(this.searchQuery.toLowerCase());
        });
      }
    },
    openDialog() {
      this.dialog = true; // Open the dialog
    },
    closeDialog() {
      this.dialog = false; // Close the dialog
    },
    addCard() {
      this.closeDialog();
    }
  }
}
</script>

<style scoped>
.v-card {
  height: auto;
}

.add-card-btn {
  position: fixed;
  bottom: 20px;
  right: 20px;
}
</style>
