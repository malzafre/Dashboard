<template>
    <v-navigation-drawer expand-on-hover rail style="background-color: #1e1e1e; color: white;">
        <v-list>
            <v-list-item prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg" title="Rayven Clores"
                subtitle="System Administrator"></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
            <v-list-item prepend-icon="mdi-view-dashboard" title="Dashboard" value="dashboard"
                to="/dashboard"></v-list-item>
            <v-list-item prepend-icon="mdi-file-document-outline" title="New Application" value="new_application"
                to="/apply"></v-list-item>
            <v-list-item prepend-icon="mdi-account-group-outline" title="Applicants" value="applicants"
                to="/applicants"></v-list-item>
            <v-list-item prepend-icon="mdi-credit-card" title="Payment" value="payment" to="/payment"></v-list-item>
            <v-list-item prepend-icon="mdi-account-multiple" title="Members" value="members"
                to="/members"></v-list-item>
            <v-list-item prepend-icon="mdi-home" title="Accommodations" value="accommodations"
                to="/accommodations"></v-list-item>
        </v-list>

        <template v-slot:append>
            <div class="pb-2">
                <v-list-item prepend-icon="mdi-logout" title="Logout" value="logout" to="/logout"></v-list-item>
            </div>
        </template>
    </v-navigation-drawer>
</template>