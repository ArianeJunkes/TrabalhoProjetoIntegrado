<script>
import { v4 as uuid} from "uuid";
export default {
  data() {
    return {
      novo_categoria: "",
      novo_editora: "",
      categorias: [
        { id: "9a7c7c02-874d-4556-8a13-4a33c56571d1", name: "Juvenil", editoracod: "1" },
        { id: "475f6d39-5a56-4442-8a2d-5ceba6b4b807", name: "Romance", editoracod: "2" },
        { id: "874b37b6-3546-4c05-bc54-5d0fdb886d16", name: "Romance", editoracod: "3" },
        { id: "9b35ce67-a4ec-45a0-be67-1983e37bd723", name: "Romance", editoracod: "4" },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_categoria !== ""){
      const novo_id=uuid();
      this.categorias.push({
        id: novo_id,
        name: this.novo_categoria,
        editoracod: this.novo_editora,
      });
        this.novo_categoria = "";
        this.novo_editora = "";
      }
    },
    excluir(categoria){
      const indice = this.categorias.indexOf(categoria);
      this.categorias.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Categorias</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Gênero" v-model="novo_categoria" @keypress.enter="salvar" />
      <input type="text" placeholder="Código Editora" v-model="novo_editora" @keypress.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Código Editora</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="categoria in categorias" :key="categoria.id">
            <td>{{categoria.id}}</td>
            <td>{{categoria.name}}</td>
            <td>{{categoria.editoracod}}</td>
            <td>
              <button @click="excluir(categoria)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>