<template>
  <div>
    <div class="signature-visualization">
      <section class="signature-container">
        <table cellspacing="0" cellpadding="0" border="0">
          <tbody>
            <!-- Logo de Cosmo -->
            <tr>
              <td valign="top" style="padding:0">
                <a href="http://www.cosmotech.com">
                  <img
                    src="http://mailsig.cosmotech.com/logo-cosmotech.png?ct=true"
                    nosend="1"
                    border="0"
                    height="117"
                    alt="Cosmo Tech"
                    title="Cosmo Tech"
                  />
                </a>
              </td>
              <td style="padding-left:10pt">
                <table cellspacing="0" cellpadding="0" border="0">
                  <tbody>
                    <!-- Nom + Prénom + Equipe + Poste -->
                    <tr>
                      <td valign="top">
                        <span>{{ firstName }} {{ lastName }}</span>
                        <br />
                        <span v-if="squad">{{ squad }}&nbsp;|&nbsp;</span>
                        <span>{{ jobTitle }}</span>
                      </td>
                    </tr>

                    <!-- Mail + phones -->
                    <tr>
                      <td valign="top">
                        <!-- On affiche le numéro de téléphone portable que si un numéro est renseigné -->
                        <span v-if="mobile">Mobile: {{ mobile }} |</span>
                        Office: {{ fixe }}
                        <br />
                        <a :href="linkToMail">{{ mail }}</a> |
                        <a href="http://www.cosmotech.com">www.cosmotech.com</a>
                        <br />5 Passage du Vercors 69007 Lyon, France
                      </td>
                    </tr>

                    <!-- Lien vers les réseaux sociaux -->
                    <tr>
                      <td valign="top">
                        <a href="https://twitter.com/cosmotechweb">
                          <img
                            src="http://mailsig.cosmotech.com/icon-twitter.png?ct=true"
                            nosend="1"
                            border="0"
                            width="20"
                            height="20"
                            alt="Twitter"
                          />
                        </a>&nbsp;
                        <a href="https://www.linkedin.com/company/cosmotechweb/">
                          <img
                            src="http://mailsig.cosmotech.com/icon-linkedin.png?ct=true"
                            nosend="1"
                            border="0"
                            width="20"
                            height="20"
                            alt="LinkedIn"
                          />
                        </a>&nbsp;
                        <a href="https://www.youtube.com/channel/UCYy1wSrTiCXx6BQKGTOsmfA">
                          <img
                            src="http://mailsig.cosmotech.com/icon-youtube.png?ct=true"
                            nosend="1"
                            border="0"
                            width="20"
                            height="20"
                            alt="YouTube"
                          />
                        </a>&nbsp;
                        <a href="https://www.facebook.com/cosmotechweb/">
                          <img
                            src="http://mailsig.cosmotech.com/icon-facebook.png?ct=true"
                            nosend="1"
                            border="0"
                            width="20"
                            height="20"
                            alt="Facebook"
                          />
                        </a>
                      </td>
                    </tr>
                  </tbody>
                </table>
              </td>
            </tr>
          </tbody>
        </table>
      </section>
    </div>
    <div class="cosmo-background">
      <img src="../assets/cosmo.png" alt="COSMO" />
    </div>
  </div>
</template>

<script>
export default {
  name: "signatureVisualization",
  props: [
    "firstName",
    "lastName",
    "squad",
    "jobTitle",
    "mail",
    "mobile",
    "fixe",
    "isHidden"
  ],
  computed: {
    linkToMail: function() {
      // Il n'est pas directement possible de passer une variable à l'attribut HTMl "mailto:"
      // Nous construisons donc ici le lien
      return "mailto: " + this.mail;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.signature-visualization {
  position: absolute;
  top: 0;
  left: 0;

  height: 100vh;
  width: 100vw;

  background-color: #0d3a58;

  display: flex;
  align-items: center;
  justify-content: center;

  .signature-container {
    height: 90vh;
    width: 90vh;

    z-index: 2;

    border-radius: 50%;
    background-color: #f6f6f6;

    display: flex;
    align-items: center;
    justify-content: center;
  }

  tr {
    padding: 0px;
    text-align: left;
    color: #292f33;
    font-size: 9pt;
    font-family: "Arial", sans-serif;
    font-weight: normal;
  }
}

.cosmo-background {
  position: absolute;
  top: 0;
  left: 0;
  height: 100vh;
  width: 100vw;

  display: flex;
  align-items: flex-end;
  justify-content: center;

  z-index: 1;
  img {
    max-width: 100vw;
  }
}
</style>
