<template>
    <v-container style="padding: 0;">
        <v-row no-gutters style="gap: 40px;">
            <v-col cols="2.5">
                <v-card class="card" link to="/payment">
                    <h1 class="fee-amount"> <span class="peso-sign">₱</span>
                        200,000.00</h1>
                    <h3 class="title">Total Fees</h3>
                </v-card>

            </v-col>

            <v-col cols="2.5">
                <v-card class="card" link to="/members">
                    <h1 class="fee-amount">80</h1>

                    <h3 class="title">Active Members</h3>

                </v-card>
            </v-col >

            <v-col cols="2.5">
                <v-card class="card" link to="/accommodations">
                    <h1 class="fee-amount">160</h1>

                    <h3 class="title">Accommodations</h3>

                </v-card>
            </v-col>

            <v-col cols="2.5">
                <v-card class="card" link to="/applicants">
                    <h1 class="fee-amount">10</h1>

                    <h3 class="title">Pending application</h3>

                </v-card>
            </v-col>
        </v-row>
    </v-container>
</template>

<style scoped>
.card {
    display: flex;
    flex-direction: column;
    height: 170px;
    border-left: 25px #607683 solid;
    box-shadow: 0px 0px 10px 1px rgba(0, 0, 0, 0.3);
}

.fee-amount {
    color: #607683;
    padding: 0 5px;
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
}

.title {
    color: #607683;
    border-top: 1px solid #607683;
    height: 70px;
    width: 100%;
    padding: 0 5px;
    display: flex;
    align-items: center;
}

h1 {
    font-size: 45px;
}
</style>