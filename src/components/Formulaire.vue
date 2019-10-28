<template>
  <div>
    <div class="formulaire" v-show="visualizationIsHidden">
      <section class="app-presentation">
        <div class="logo-container">
          <img src="../assets/logo.png" alt />
        </div>
        <article>
          <p>
            Utilisez le formulaire pour saisir vos informations personnelles.
            Les champs
            <span
              class="orange"
            >en orange</span>
            sont obligatoires.
          </p>
          <p>
            Vous pouvez copier/coller le résultat dans Gmail :
            <span class="blue">Setting >&nbsp;</span>
            <span class="blue">General >&nbsp;</span>
            <span class="blue">Signature</span>
          </p>
          <p>Merci d'utiliser Google Chrome, Mozilla Firefox ne permettant pas de copier convenablement le résultat.</p>
        </article>
      </section>

      <section class="form-container" v-show="visualizationIsHidden">
        <article>
          <input
            type="text"
            class="important"
            name="First Name"
            v-model="firstName"
            placeholder="Prénom"
          />
          <input
            type="text"
            class="important"
            name="Last name"
            v-model="lastName"
            placeholder="Nom"
          />
        </article>
        <article>
          <input type="text" name="Squad" v-model="squad" placeholder="Equipe" />
          <input type="text" name="Job title" v-model="jobTitle" placeholder="Intitulé du poste" />
        </article>
        <article>
          <input type="text" name="Mobile" v-model="mobile" placeholder="Tél. mobile" />
          <input type="text" class="important" name="Fixe" v-model="fixe" placeholder="Tél. fixe" />
        </article>
        <input
          type="text"
          class="important mail-input"
          name="Mail"
          v-model="mail"
          placeholder="Email"
        />
        <button @click="showSignatureVisualization()">Générer</button>
      </section>
    </div>
    <div :class="signatureVisualizationState">
      <signature-visualization
        v-bind:firstName="firstName"
        v-bind:lastName="lastName"
        v-bind:squad="squad"
        v-bind:jobTitle="jobTitle"
        v-bind:mail="mail"
        v-bind:mobile="mobile"
        v-bind:fixe="fixe"
        v-bind:visualizationIsHidden="visualizationIsHidden"
      />
    </div>
    <div class="close-signature-visualization" v-show="!visualizationIsHidden">
      <svg
        role="img"
        xmlns="http://www.w3.org/2000/svg"
        width="1000mm"
        height="1000mm"
        viewBox="0 0 1000 1000"
        style="max-width:1.6em; height: auto;"
        @click="showSignatureVisualization()"
      >
        <path
          id="path"
          style="opacity:1;vector-effect:none;fill:#f6f6f6;fill-opacity:1;"
          d="M 500 0C 224 0 0 224 0 500C 0 776 224 1000 500 1000C 776 1000 1000 776 1000 500C 1000 224 776 0 500 0C 500 0 500 0 500 0M 500 75C 735 75 925 265 925 500C 925 735 735 925 500 925C 265 925 75 735 75 500C 75 265 265 75 500 75C 500 75 500 75 500 75 M 300 262C 310 262 319 266 327 273C 327 273 500 447 500 447C 500 447 673 273 673 273C 680 266 690 262 699 262C 715 262 729 271 735 285C 741 299 738 316 727 327C 727 327 553 500 553 500C 553 500 727 673 727 673C 736 683 740 697 737 710C 733 723 723 733 710 737C 697 740 683 736 673 727C 673 727 500 553 500 553C 500 553 327 727 327 727C 317 736 303 740 290 737C 277 733 267 723 263 710C 260 697 264 683 273 673C 273 673 447 500 447 500C 447 500 273 327 273 327C 263 316 259 300 265 286C 271 271 284 262 300 262C 300 262 300 262 300 262"
          transform
        />
      </svg>
    </div>
  </div>
</template>

<script>
import signatureVisualization from "./Signature-Visualization.vue";

export default {
  name: "Formulaire",
  components: {
    signatureVisualization
  },
  data: () => {
    return {
      firstName: null,
      lastName: null,
      mail: null,
      mobile: null,
      fixe: "+33 4 37 66 71 57",
      squad: null,
      jobTitle: null,
      visualizationIsHidden: true
    };
  },
  computed: {
    signatureVisualizationState: function() {
      return this.visualizationIsHidden ? "hidden" : "displayed";
    }
  },
  methods: {
    showSignatureVisualization() {
      this.visualizationIsHidden = !this.visualizationIsHidden;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.formulaire {
  display: flex;
  align-items: center;
  justify-content: center;

  .app-presentation {
    max-width: 30%;
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    .logo-container {
      margin-bottom: 5rem;
      img {
        transform: rotate(-20deg);
      }
    }

    article {
      margin-left: 3rem;
      font-family: "Fira Sans", sans-serif;
      color: #f6f6f6;
      text-align: justify;
    }
  }

  .form-container {
    min-height: 100vh;
    min-width: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    left: 35%;

    input {
      margin: 1rem;
      padding: 1rem 0 0.5rem 1rem;
      background: none;
      border: none;
      border-bottom: 2px solid white;
      outline: none;

      font-family: "Fira Sans", sans-serif;
      font-size: 1rem;
      color: white;

      transition-duration: 0.1s;
    }

    .mail-input {
      width: 40%;
    }

    ::-webkit-input-placeholder {
      /* Chrome/Opera/Safari */
      color: white;
    }
    ::-moz-placeholder {
      /* Firefox 19+ */
      color: white;
    }

    input:focus {
      color: #9effff;
      border-bottom: 2px solid #9effff;
      font-weight: bold;
    }

    input:focus::-webkit-input-placeholder {
      color: #9effff;
    }

    .important {
      border-bottom: 2px solid #ff9d00;
    }

    button {
      background: none;
      outline: none;
      cursor: pointer;

      margin-top: 3rem;
      padding-bottom: 1rem;

      border: 1px solid #0d3a58;
      border-radius: 5px;
      font-family: "Pacifico", cursive;
      font-size: 2.5rem;
      text-decoration: underline;
      color: #f6f6f6;
    }

    button:hover {
      color: #9effff;
      border: 1px solid #9effff;
      box-shadow: 0 20px 50px rgba(20, 220, 247, 0.7);
      transition-duration: 0.5s;
    }
  }
}

.close-signature-visualization {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 3;

  padding: 5rem 5rem 0 0;

  svg {
    transition-duration: 0.5s;
  }

  svg:hover {
    transform: scale(1.2);
    cursor: pointer;
  }
}

@media screen and (max-width: 1300px) {
  .formulaire {
    flex-direction: column;
    .app-presentation {
      max-width: 60%;
      min-height: 0;

      flex-direction: row;
      padding-top: 2rem;

      .logo-container {
        margin: 0;
      }

      img {
        max-height: 200px;
      }
    }

    .form-container {
      min-height: 0;
      margin-top: 3rem;

      input {
        border-bottom: 2px solid white;
      }

      .important {
        border-bottom: 2px solid #ff9d00;
      }

      button {
        font-size: 2rem;
      }
    }
  }
}
</style>
