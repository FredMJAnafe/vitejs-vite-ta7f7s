<template>
  <div
    class="ParametDeconnexionres lienDeconnexion"
    @click="this.$router.push({ name: 'modifierProfil' })"
  >
    <font-awesome-icon icon="fa-file-invoice" />
    <span class="texteParametres">Param&egrave;tres</span>
  </div>
</template>

<script>
import connexionAPIService from '@/services/connexionAPI.service.vue';
import construitURLService from '@/services/construitURL.service.vue';
import configuration from '@/administration/configuration.vue';

export default {
  name: 'BoutonParametres',
};
</script>

<style scoped></style>
