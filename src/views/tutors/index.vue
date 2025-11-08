<template>
  <div class="mb-2">
    <breadcrumbs>
      <template v-slot:model> Tutores </template>
      <template v-slot:action> Lista de Tutores </template>
    </breadcrumbs>
  </div>
  <div class="card w-full bg-base-100 shadow-sm card-border">
    <div class="card-body">
      <div class="overflow-x-auto">
        <div class="flex">
          <div class="flex-1 mb-5 text-2xl">Tutores</div>
          <button class="btn btn-second" @click="adicionar">Adicionar</button>
        </div>
        <table class="table">
          <!-- head -->
          <thead>
            <tr>
              <th>
                <label>
                  <input type="checkbox" class="checkbox" />
                </label>
              </th>
              <th>Nome</th>
              <th>Endereço</th>
              <th>Telefone</th>
              <th>Ações</th>
            </tr>
          </thead>
          <tbody>
            <!-- row 1 -->
<<<<<<< HEAD
            <tr v-for="tutor in tutores" :key="tutor.id">
=======
            <tr v-for="item in tutores" :key="item.data.nome">
>>>>>>> upstream/turma02-localbase
              <th>
                <label>
                  <input type="checkbox" class="checkbox" />
                </label>
              </th>
              <td>
                <div class="flex items-center gap-3">
                  <div class="avatar">
                    <div class="mask mask-squircle h-12 w-12">
                      <img
                        src="https://img.daisyui.com/images/profile/demo/2@94.webp"
                        alt="Avatar Tailwind CSS Component"
                      />
                    </div>
                  </div>
                  <div>
<<<<<<< HEAD
                    <div class="font-bold">{{ tutor.nome }}</div>
                    <div class="text-sm opacity-50">
                      {{ tutor.endereco.cidade ?? "Cliente sem cidade" }}
                    </div>
                  </div>
                </div>
              </td>
              <td>
                {{ tutor.endereco.logradouro }} {{ tutor.endereco.numero ?? "S/N" }}
                {{ tutor.endereco.cep }} {{ tutor.endereco.complemento }}
                <br />
                <span class="badge badge-ghost badge-sm"
                  >{{ tutor.endereco.cidade }}/{{ tutor.endereco.estado }}</span
                >
              </td>
              <td>
                <div
                  v-for="telefone in tutor.telefones"
                  :key="telefone"
                  class="badge badge-xs badge-dash flex m-1"
                >
                  {{ telefone }}
                </div>
              </td>
              <th>
                <button class="btn btn-ghost btn-xs">details</button>
=======
                    <div class="font-bold">{{ item.data?.nome }}</div>
                    <div class="text-sm opacity-50">United States</div>
                  </div>
                </div>
              </td>
              <td>
                Zemlak, Daniel and Leannon
                <br />
                <span class="badge badge-ghost badge-sm">Desktop Support Technician</span>
              </td>
              <td>Purple</td>
              <th>
                <router-link
                  class="btn btn-info btn-xs"
                  :to="{ name: 'tutors.edit', params: { id: item.key } }"
                  >editar</router-link
                >
                <a href="#my_modal_1" class="btn btn-error btn-xs"> Deletar </a>
                <div class="modal" role="dialog" id="my_modal_1">
                  <div class="modal-box">
                    <h3 class="text-lg font-bold">Hello!</h3>
                    <p class="py-4">This modal works with anchor links</p>
                    <div class="modal-action">
                      <a href="#" class="btn">Yay!</a>
                    </div>
                  </div>
                </div>
>>>>>>> upstream/turma02-localbase
              </th>
            </tr>
          </tbody>
          <!-- foot -->
        </table>
      </div>
    </div>
  </div>
</template>

<script setup>
import breadcrumbs from "@/components/breadcrumbs.vue";
<<<<<<< HEAD
import { ref, onMounted } from "vue";
import { useRouter } from "vue-router";
import Localbase from "localbase";

let db;
onMounted(() => {
  db = new Localbase("db");
=======
import DBService from "@/services/DBService";
import { onMounted, ref, useTemplateRef } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();
const dialog = useTemplateRef("my_modal_1");

onMounted(async () => {
>>>>>>> upstream/turma02-localbase
  capturarTutores();
});

const tutores = ref([]);

<<<<<<< HEAD
const capturarTutores = async () => {
  tutores.value = await db.collection("tutores").get();
};

const router = useRouter();

const adicionar = () => {
  router.push({ name: "tutors.add" });
};
=======
const adicionar = () => {
  router.push({ name: "tutors.add" });
};

const capturarTutores = async () => {
  tutores.value = await DBService.listar("tutores");
};

function manipularModal() {
  dialog.showModal();
}
>>>>>>> upstream/turma02-localbase
</script>

<style lang="scss" scoped></style>
