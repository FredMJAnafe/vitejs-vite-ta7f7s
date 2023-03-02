<template>
  <section class="card">
    <div class="cardHead">
      <h2>{{montantTotal}}</h2>
      <font-awesome-icon class="fontIcone" icon="fa-money-bill-transfer" />
    </div>
    <div class="contenuCard">
      <small>Montant à solder <strong>{{this.$props.montant.intitule}}</strong></small>
      <div class="indicateurCard">
        <div class="affichageIndicateurCard"></div>
      </div>
      <div class="inputBoxFacturier">
      <span class="detailFacturier">Début </span>
      <input
        id="dateNaissanceContrat"
        type="date"
        name="dateDebut"
        @input="this.SiContratAvenant"
        required
      />
    </div>
    <div class="inputBoxFacturier">
      <span class="detailFacturier">Fin </span>
      <input
        id="dateNaissanceContrat"
        type="date"
        name="dateFin"
        @input="this.SiContratAvenant"
        required
      />
    </div>
    </div>
  </section>
</template>

<script>
export default { 
  name: "fenetreMontant",
  computed:{
    montantTotal() {
      return this.montant.montant;
    }
  },
  props:{
    montant:Object
  }
}
</script>

<style scoped>
section.card {
  max-width:250px;
  min-width: 170px;
}
.cardHead{
  display: flex;
  justify-content: space-between;
  margin-left: 1em;
  margin-right: 1em;
  align-items: flex-start;
}
.fontIcone{
  font-size: 2rem;
  color: var(--color-dark);
}

.cardHead h2{
  font-size: 18px;
  color: #555;
  line-height:1;
  margin-top: 8px;
}

.contenuCard{
  padding-left: 1rem;
  color: #555555;
  font-weight: 400;
  text-align:left;
}
.contenuCard .inputBoxFacturier {
  text-align:right;
}
.contenuCard input{
  max-width:100px;
  margin:3px;
}

</style>