<template>
  <div class="landing-page">
    <!-- Top Section -->
    <header class="top-buttons">
      <button @click="readQrCode" class="btn-top-left">📱 Ler QR Code</button>
      <button @click="shareLink" class="btn-top-right">🔗 Compartilhar Link</button>
    </header>

    <!-- Proprietário -->
    <section class="owner-info">
      <img class="img-perfil" src="./assets/foto-perfil.jpg" alt="">
      <h1>{{ owner.name }}</h1>
      <p class="motto">"Tradição e estilo em cada corte"</p>
      <p class="text1">{{ owner.address }}</p>
      <p class="text2">{{ owner.city }}</p>
    </section>

    <!-- Contatos -->
    <section class="contact-buttons">
      <button @click="saveContact">Salvar</button>
      <button @click="callOwner">Ligar</button>
    </section>

    <!-- Ações -->
    <section class="action-buttons">
      <img class="whats"@click="openWhatsApp" src="./assets/img-whats.png" alt="">
      <img class="wifi"@click="openWifi" src="./assets/img-wifi.png" alt="Wi-fi">
      <img class="pix"@click="openPix" src="./assets/img-pix.png" alt="">
    </section>

    <!-- Agendamentos e Redes Sociais -->
    <section class="social-buttons">
      <button class="btn-agendamentos" @click="scheduleAppointment">Agende o seu horário</button>
      <button class="btn-agendamentos" @click="reviewOnGoogle">Avalie no Google</button>
      <button class="btn-agendamentos" @click="openInstagram">Instagram</button>
      <button class="btn-agendamentos" @click="copyPixKey">Chave Pix (Copiar)</button>
    </section>

    <!-- Cards de Cortes -->
    <section class="cuts">
      <div 
        v-for="cut in cuts" 
        :key="cut.id" 
        class="cut-card" 
        @click="selectCut(cut)"
      >
        <h3>{{ cut.title }} - R$ {{ cut.price }}</h3>
        <p>{{ cut.description }}</p>
        <img :src="cut.image" :alt="cut.title" class="cut-img" />
      </div>
    </section>
  </div>
</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css';
import imgMandrak from './assets/img-mandrake.jpg'
import imgBoyzao from './assets/img-boyzao.jpg';

export default {
  data() {
    return {
      owner: {
        name: "Lucas Garcia",
        address: "Rua Teste Giovani, 1562",
        city: "Osasco-SP",
      },
      cuts: [
        {
          id: 1,
          title: "Corte Mandrak",
          price: "00,00",
          description: "Estilo moderno e bem definido.",
          image: imgMandrak,
        },
        {
          id: 2,
          title: "Corte Degradê",
          price: "00,00",
          description: "Estilo moderno e bem definido.",
          image: imgBoyzao,
        },
      ],
    };
  },
  methods: {
    readQrCode() {
      alert("Função para ler QR Code.");
    },
    shareLink() {
      alert("Função para compartilhar o link.");
    },
    saveContact() {
      alert("Contato salvo com sucesso!");
    },
    callOwner() {
      window.location.href = "tel:+551199999999";
    },
    openWhatsApp() {
      window.open("https://wa.me/551199999999", "_blank");
    },
    openWifi() {
      alert("Abrir informações de Wi-Fi.");
    },
    openPix() {
      alert("Abrir Pix.");
    },
    scheduleAppointment() {
      alert("Função para agendar horário.");
    },
    reviewOnGoogle() {
      window.open("https://g.page/link-google-review", "_blank");
    },
    openInstagram() {
      window.open("https://instagram.com/username", "_blank");
    },
    copyPixKey() {
      navigator.clipboard.writeText("sua-chave-pix-aqui");
      alert("Chave Pix copiada!");
    },
    selectCut(cut) {
      alert(`Selecionado: ${cut.title}`);
    },
  },
};
</script>

<style>




/* Estilos gerais */
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.landing-page {
  background-color: rgba(0, 0, 0, 0.788);
  text-align: center;
  padding: 1rem;
}

/* Top Buttons */
.top-buttons button {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  width: 100%;
}

/* Proprietário */
.img-perfil {
  width: 200px;
}

.owner-info .owner-img {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  margin: 1rem auto;
}
.owner-info .shop-img {
  width: 100%;
  max-width: 400px;
  margin: 1rem auto;
}
.owner-info h1 {
  margin: 18px 0;
  margin-top: 1rem;
  color: white;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  font-weight: 700;
}
.owner-info p {
  margin: 5px 0;
  color: white;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

/* Botões de contato */
.contact-buttons button,
.action-buttons button,
.social-buttons button {
  margin: 10px;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.wifi {
    height: 40px;
    width: 40px;
  }


/* Cards */
.cut-card {
  margin: 20px auto;
  padding: 15px;
  border: 1px solid #ddd;
  border-radius: 8px;
  max-width: 400px;
  text-align: left;
}
.cut-card img {
  width: 100%;
  margin-top: 10px;
}

@media (max-width:500px) {

  .landing-page {
    border: none;
    border-radius: 2rem;
  }

  .img-perfil {
    margin-top: 4rem;
    width: 100px;
    border: none;
    border-radius: 3rem;
    transition: scale(1);
  }

  h1 {
    font-size: 20px;
  }

  .img-perfil:hover {
    font-size: 20px;
    transform: scale(1.1);
  }

  .top-buttons {
    display: flex;
    justify-content: center;
    gap: 4rem;
    font-size: 8px;
    width: 100%;
  }

  .top-buttons .btn-top-left {
    height: 40px;
    width: 80px;
    font-size: 10px;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-weight: 700;
    display: flex;
  }

  .top-buttons .btn-top-right {
    display: flex;
    height: 40px;
    width: 100px;
    font-size: 10px;
    font-weight: 700;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
  }

  button {
    border: none;
    border-radius: 1rem;
    background: linear-gradient(to right, #ffffff, #de3d3b);
  }

  .text1 {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    color: #de3d3b;
    padding-top: 0.5rem;
  }

  .action-buttons {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 1rem;
  }

  .whats {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 40px;
    width: 50px;
    color: #ddd;
    margin: 12px;
    padding: 4px;
    background-color: #de3d3b;
    border: none;
    border-radius: 1rem;
    box-shadow: 0 0 2px #de3e3bb0;
  }

  .wifi {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 60px;
    color: #ddd;
    margin: 12px;
    padding: 4px;
    background-color: #de3d3b;
    border: none;
    border-radius: 1rem;
    box-shadow: 0 0 2px #de3e3bb0;
  }

  .pix {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 70px;
    color: #ddd;
    margin: 12px;
    padding: 4px;
    background-color: #de3d3b;
    border: none;
    border-radius: 1rem;
    box-shadow: 0 0 2px #de3e3bb0;
  }

  .social-buttons {
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
    margin-top: 2rem;
  }

  .btn-agendamentos {
    width: 100%;
    border: none;
    border-radius: 1px solid rgb(236, 227, 227);
    font-family: Verdana;
    font-size: 20px;
    font-weight: 800;
  }

  .cut-card {
    background-color: #de3e3ba9;
  }

  h3 {
    color: white;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    font-size: 16px;
    font-weight: 800;
  }

  p {
    color: white;
  }
}

</style>
