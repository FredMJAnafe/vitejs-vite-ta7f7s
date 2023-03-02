<template>
  <section class="sidebar">
    <div class="side-header">
      <div class="logo-entreprise">
        <img
          :src="this.logoEntreprise"
          crossOrigin="Anonymous"
          alt="entreprise"
        />
      </div>
    </div>
    <div class="side-content">
      <div class="profil">
        <div class="photoProfil">
          <img
            v-if="this.utilisateur.photoProfil"
            :src="this.utilisateur.photoProfil"
          />
          <font-awesome-icon v-else class="fontIcone" icon="fa-user-edit" />
        </div>
        <h4>{{ this.utilisateur.nom }}</h4>
        <span> {{ this.utilisateur.prenom }} </span>
      </div>
    </div>

    <div class="side-menu">
      <ul>
        <li class="elementLienNav">
          <BoutonParametres> </BoutonParametres>
        </li>
        <li class="elementLienNav" id="elementDeconnexion">
          <BoutonDeconnexion> </BoutonDeconnexion>
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
//import logoEntreprise from '#/logo0_small.png'
import App from '@/App.vue';
import BoutonDeconnexion from '@/components/Controler/connexion/BoutonDeconnexion.vue';
import BoutonParametres from '@/components/Controler/connexion/BoutonParametres.vue';

export default {
  name: 'navBarFacturier',
  data() {
    return {
      logoEntreprise: App.data().pab + '/logo0_small.png',
    };
  },
  props: {
    utilisateur: Object,
  },
  components: {
    BoutonDeconnexion,
    BoutonParametres,
  },
};
</script>

<style scoped>
section.sidebar {
  position: fixed;
  height: 100%;
  width: 165px;
  left: 0;
  bottom: 0;
  top: 0;
  z-index: 100;
  background: var(--color-dark);
}

div.side-header {
  background: white;
  height: 120px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.logo-entreprise img {
  height: 90px;
  width: 90px;
}

.profil img {
  height: 90px;
  width: 90px;
  border-radius: 50%;
}

div.profil {
  text-align: center;
  padding: 1rem 0rem;
  color: white;
}

.photoProfil {
  height: 90px;
  width: 90px;
  display: inline-block;
  margin: 0 auto;
  background-repeat: no-repeat;
  background-size: cover;
  border-radius: 50%;
  color: white;
}
.photoProfil .fontIcone {
  height: 80px;
}
div.profil h4 {
  color: white;
  font-weight: 300;
}

div.side-menu li {
  position: relative;
  left: -15px;
  display: block;
}

div.side-menu span {
  display: block;
  text-align: center;
  font-size: 1rem;
}

#elementDeconnexion {
  border: solid red 2px;
}
#elementDeconnexion:hover {
  box-shadow: 0px 0px 3px 1px red;
}

.elementLienNav {
  border-radius: 6px 0 6px 0;
  background-color: #3d5276;
  padding: 10px;
  font-size: 16px;
}
li.elementLienNav {
  margin-bottom: 1.2em;
  border: solid white 1px;
  text-decoration: none;
  color: white;
}

.elementLienNav:hover {
  text-decoration: none;
  color: var(--rose-pastel);
  box-shadow: 0px 0px 3px 1px white;
}

.lienDeconnexion{
  padding-left: 20px;
  padding-right: 20px;
}
</style>
