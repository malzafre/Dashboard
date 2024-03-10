<template>
  <v-container class="contents">
    <v-container class="content-title">
      <hr class="title-line-left">
      <h1>Apply</h1>
      <hr class="title-line-right">
    </v-container>
    <v-row class="Container">
      <v-col cols="12" sm="10" md="8" lg="8">
        <v-container class="form-container">
          <h2>ACOTA MEMBERSHIP APPLICATION</h2>
          <v-row>
            <v-col cols="12" md="4">
              <v-text-field v-model="firstName" label="First Name" outlined required></v-text-field>
            </v-col>
            <v-col cols="12" md="4">
              <v-text-field v-model="middleName" label="Middle Name" outlined></v-text-field>
            </v-col>
            <v-col cols="12" md="4">
              <v-text-field v-model="lastName" label="Last Name" outlined required></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12" md="6">
              <v-text-field v-model="email" label="Email" outlined required></v-text-field>
            </v-col>
            <v-col cols="12" md="6">
              <v-text-field v-model="contactNumber" label="Contact Number" outlined type="number"
                required></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12" md="6" class="d-flex justify-center align-center">
              <v-menu v-model="birthdayMenu" :close-on-content-click="false" :nudge-right="40" class="date-layout"
                transition="scale-transition" offset-y>
                <template v-slot:activator="{ on, attrs }">
                  <v-text-field v-model="formattedBirthdate" label="Birthday" outlined readonly v-bind="attrs" v-on="on"
                    append-icon="mdi-calendar" @click:append="birthdayMenu = !birthdayMenu"></v-text-field>
                </template>
                <v-date-picker v-model="birthdate" no-title no-time scrollable></v-date-picker>
              </v-menu>
            </v-col>
            <v-col cols="12" md="6">
              <v-text-field v-model="age" label="Age" outlined type="number"></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12" md="6">
              <v-text-field v-model="address" label="Address" outlined required></v-text-field>
            </v-col>
            <v-col cols="12" md="6">
              <v-select v-model="gender" :items="genderOptions" label="Gender" outlined required></v-select>
            </v-col>
          </v-row>
          <v-row>
            <v-col cols="12" md="6">
              <v-select v-model="civilStatus" :items="civilStatusOptions" label="Civil Status" outlined
                required></v-select>
            </v-col>
          </v-row>
          <v-row class="termsandconditions">
            <v-col cols="12">
              <v-checkbox v-model="agreeTerms" label="I Agree to the Terms and Conditions" outlined></v-checkbox>
            </v-col>
          </v-row>
          <v-row class="PrivacyPolicy">
            <v-col cols="12">
              <v-checkbox v-model="agreePrivacy" label="I Agree to Privacy Policy" outlined></v-checkbox>
            </v-col>
          </v-row>
          <v-row class="submit-row">
            <v-col cols="12" class="text-center">
              <v-btn color="grey" @click="validateForm" class="submit-button">Submit</v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-col>
    </v-row>

    <v-dialog v-model="showReceipt" max-width="600px">
      <v-card>
        <v-card-title class="headline">Confirmation</v-card-title>
        <v-card-text>
          <div>
            <p><strong>First Name:</strong> {{ firstName }}</p>
            <p><strong>Middle Name:</strong> {{ middleName }}</p>
            <p><strong>Last Name:</strong> {{ lastName }}</p>
            <p><strong>Email:</strong> {{ email }}</p>
            <p><strong>Contact Number:</strong> {{ contactNumber }}</p>
            <p><strong>Birthday:</strong> {{ formattedBirthdate }}</p>
            <p><strong>Age:</strong> {{ age }}</p>
            <p><strong>Address:</strong> {{ address }}</p>
            <p><strong>Gender:</strong> {{ gender }}</p>
            <p><strong>Civil Status:</strong> {{ civilStatus }}</p>
          </div>
          <v-row class="copy-application">
            <v-col cols="12">
              <v-checkbox v-model="copyApplication" label="Send me a copy of this application" outlined></v-checkbox>
            </v-col>
          </v-row>
        </v-card-text>
        <v-card-actions class="Receiptbutton">
          <v-btn class="ConfirmButton" @click="confirmForm">Confirm</v-btn>
          <v-btn text @click="showReceipt = false">Cancel</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>

  </v-container>
</template>

<script>
export default {
  data() {
    return {
      firstName: '',
      middleName: '',
      lastName: '',
      email: '',
      contactNumber: '',
      birthdate: null,
      age: null,
      address: '',
      gender: null,
      civilStatus: null,
      genderOptions: ['Male', 'Female'],
      civilStatusOptions: ['Single', 'Married', 'Divorced', 'Widowed'],
      birthdayMenu: false,
      agreeTerms: false,
      agreePrivacy: false,
      showReceipt: false,
      copyApplication: false
    };
  },
  computed: {
    formattedBirthdate() {
      if (!this.birthdate) return null;
      const date = new Date(this.birthdate);
      const options = { month: 'short', day: '2-digit', year: 'numeric' };
      return date.toLocaleDateString('en-US', options);
    }
  },
  methods: {
    validateForm() {
      if (!this.agreeTerms) {
        alert('Please agree to the terms and conditions.');
      } else if (!this.agreePrivacy) {
        alert('Please agree to the privacy policy.');
      } else if (!this.firstName || !this.lastName || !this.email || !this.contactNumber || !this.address || !this.gender || !this.civilStatus) {
        alert('Please fill in all required fields.');
      } else {
        this.showReceipt = true;
      }
    },
    confirmForm() {
      console.log('Form submitted!'); 0
      this.showReceipt = false;
      alert('Congrats! Your form submitted successfully.');
    }
  }
};
</script>

<style scoped>
.contents {
  height: 100vh;
  width: 100vw;
  margin: 0;
  padding: 0;
}

.Container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-left: 15px;
  height: 90%;
  padding: 0 10px;
}

.content-title {
  width: 100%;
  display: flex;
  align-items: center;
}

h1 {
  margin: 0 10px 0 10px;
  color: #607683;
}

h2 {
  background-color: #607683;
  text-align: center;
  margin: 0 10px 15px 10px;
  color: #ffffff;
}

.title-line-left,
.title-line-right {
  border: 3px solid #607683;
}

.title-line-left {
  border: 3px solid #607683;
  width: 200px;
}

.title-line-right {
  border: 3px solid #607683;
  width: 100%;
}

.form-container {
  height: auto;
  width: auto;
  padding: 30px;
  background-color: #f2f2f2;
  border-radius: 10px;
  box-shadow: 0 5px 10px #0000005e;
}

.termsandconditions {
  margin-top: -70px;
  margin-bottom: -70px;
}

.PrivacyPolicy {
  margin-top: -70px;
  margin-bottom: -70px;
}

.headline {
  text-align: center;
  color: #ffffff;
  background-color: #607683;
}

.Receiptbutton {
  justify-content: center;
  align-items: center;
}

.ConfirmButton {
  color: #ffffff;
  background-color: gray;
}

.ConfirmButton:hover {
  background-color: #607683 !important;
}

.submit-row {
  margin-top: 20px;
}

.submit-button:hover {
  background-color: #607683 !important;
}

.date-layout {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.3);
  z-index: 100;
}
</style>
