<template>
<<<<<<< HEAD
  <div class="w-full">
    <fieldset class="fieldset bg-base-200 border-base-300 rounded-box w-full border p-4">
      <legend class="fieldset-legend">Adicionando tutores</legend>

      <label class="label">Nome</label>
      <input
        type="text"
        class="input w-full"
        placeholder="Nome completo"
        v-model="form.nomeCompleto"
      />

      <label class="label">Logradouro</label>
      <input type="text" class="input w-full" placeholder="Logradouro" v-model="form.logradouro" />

      <label class="label">Número</label>
      <input type="text" class="input w-full" placeholder="Número" v-model="form.numero" />

      <label class="label">Bairro</label>
      <input type="text" class="input w-full" placeholder="Bairro" v-model="form.bairro" />

      <label class="label">CEP</label>
      <input type="text" class="input w-full" placeholder="CEP" v-model="form.cep" />

      <label class="label">Complemento</label>
      <input
        type="text"
        class="input w-full"
        placeholder="Complemento"
        v-model="form.complemento"
      />

      <label class="label">Cidade</label>
      <input type="text" class="input w-full" placeholder="Cidade" v-model="form.cidade" />

      <label class="label">Estado</label>
      <input type="text" class="input w-full" placeholder="Estado" v-model="form.estado" />

      <button class="btn btn-neutral mt-4" @click="adicionarTutor">Adicionar</button>
    </fieldset>
    <div class="toast" v-if="toastVisible">
      <div class="alert alert-info">
        <span
          ><strong>{{ nomeCompletoToast }}</strong> salvo com sucesso.</span
        >
      </div>
=======
  <fieldset class="fieldset bg-base-200 border-base-300 rounded-box w-full border p-4">
    <legend class="fieldset-legend">Adicionando Tutores</legend>

    <label class="label">Nome completo</label>
    <input
      type="text"
      class="input w-full"
      v-model="form.nomeCompleto"
      placeholder="Nome completo"
    />

    <label class="label">CEP</label>
    <input type="text" class="input w-full" v-model="form.endereco.cep" placeholder="CEP" />

    <label class="label">Bairro</label>
    <input type="text" class="input w-full" v-model="form.endereco.bairro" placeholder="Bairro" />

    <label class="label">Número</label>
    <input type="text" class="input w-full" v-model="form.endereco.numero" placeholder="Número" />

    <label class="label">Logradouro</label>
    <input
      type="text"
      class="input w-full"
      v-model="form.endereco.logradouro"
      placeholder="Logradouro"
    />

    <label class="label">Cidade</label>
    <input type="text" class="input w-full" v-model="form.endereco.cidade" placeholder="Cidade" />

    <label class="label">Estado</label>
    <input type="text" class="input w-full" v-model="form.endereco.estado" placeholder="Estado" />

    <button class="btn btn-neutral mt-4" @click="adicionarTutor">Adicionar</button>
  </fieldset>

  <div class="toast" v-if="toastVisivel">
    <div class="alert alert-info">
      <span>{{ toastMesagem }}</span>
>>>>>>> upstream/turma02-localbase
    </div>
  </div>
</template>

<script setup>
<<<<<<< HEAD
import { ref, reactive, onMounted } from "vue";
import Localbase from "localbase";

let db;
onMounted(() => {
  db = new Localbase("db");
});

const toastVisible = ref(false);
const nomeCompletoToast = ref("");
const form = reactive({
  nomeCompleto: "",
  logradouro: "",
  numero: "",
  bairro: "",
  cep: "",
  complemento: "",
  cidade: "",
  estado: "",
});

const adicionarTutor = async () => {
  try {
    await db.collection("tutores").add({
      nome: form.nomeCompleto,
      endereco: {
        logradouro: form.logradouro,
        numero: form.numero,
        bairro: form.bairro,
        cep: form.cep,
        complemento: form.complemento,
        cidade: form.cidade,
        estado: form.estado,
      },
      telefones: [],
    });
    console.log("Tutor adicionado com sucesso!");
    nomeCompletoToast.value = form.nomeCompleto;
    toastVisible.value = true;
  } catch (error) {
    console.error("Erro ao adicionar tutor:", error);
  } finally {
    // Limpar o formulário após a adição
    form.nomeCompleto = "";
    form.logradouro = "";
    form.numero = "";
    form.bairro = "";
    form.cep = "";
    form.complemento = "";
    form.cidade = "";
    form.estado = "";
  }
};
=======
import { reactive, onMounted, ref } from "vue";
import { useRouter } from "vue-router";
import DBService from "@/services/DBService";

const router = useRouter();
let toastVisivel = ref(false);
let toastMesagem = ref(null);

const form = reactive({
  nomeCompleto: null,
  endereco: {
    cep: null,
    bairro: null,
    numero: null,
    logradouro: null,
    cidade: null,
    estado: null,
  },
});

async function adicionarTutor() {
  await DBService.adicionar("tutores", {
    nome: form.nomeCompleto,
    endereco: {
      cep: form.endereco.cep,
      bairro: form.endereco.bairro,
      numero: form.endereco.numero,
      logradouro: form.endereco.logradouro,
      cidade: form.endereco.cidade,
      estado: form.endereco.estado,
    },
  }).then(() => {
    // Limpar o formulário após a adição
    toastMesagem.value = `Tutor ${form.nomeCompleto} adicionado com sucesso!`;
    form.nomeCompleto = null;
    form.endereco.cep = null;
    form.endereco.bairro = null;
    form.endereco.numero = null;
    form.endereco.logradouro = null;
    form.endereco.cidade = null;
    form.endereco.estado = null;
    toastVisivel.value = true;
    setTimeout(() => {
      toastVisivel.value = false;
      router.push("/tutors");
    }, 3000);
  });
}
>>>>>>> upstream/turma02-localbase
</script>

<style lang="scss" scoped></style>
