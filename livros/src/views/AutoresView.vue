<script>
import { v4 as uuid} from "uuid";
export default {
  data() {
    return {
      novo_autor: "",
      novo_idade: "",
      novo_editora: "",
      novo_categoria: "",
      autores: [
        { id: "9b35ce67-a4ec-45a0-be67-1983e37bd723", name: "Ruth Rocha", idadeid: "91 anos", editoracod:"1", categoria:"Juvenil" },
        { id: "475f6d39-5a56-4442-8a2d-5ceba6b4b807", name: "Kiera Cass", idadeid: "41 anos", editoracod:"2", categoria:"Romance"  },
        { id: "9a7c7c02-874d-4556-8a13-4a33c56571d1", name: "Danielle Steel", idadeid: "74 anos", editoracod:"3", categoria:"Romance"  },
        { id: "874b37b6-3546-4c05-bc54-5d0fdb886d16", name: "Colleen Hoover", idadeid: "42 anos", editoracod:"4", categoria:"Romance"  },
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_autor !== ""){
      const novo_id=uuid();
      this.autores.push({
        id: novo_id,
        name: this.novo_autor,
        idadeid: this.novo_idade,
        editoracod: this.novo_editora,
        categoria: this.novo_categoria,
      });
        this.novo_autor = "";
        this.novo_idade = "";
        this.novo_editora = "";
        this.novo_categoria = "";
      }
    },
    excluir(autor){
      const indice = this.autores.indexOf(autor);
      this.autores.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de Autores</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Nome" v-model="novo_autor" @keypress.enter="salvar" />
      <input type="text" placeholder="Idade" v-model="novo_idade" @keypress.enter="salvar" />
      <input type="text" placeholder="Código Editora" v-model="novo_editora" @keypress.enter="salvar" />
      <input type="text" placeholder="Gênero" v-model="novo_categoria" @keypress.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Idade</th>
            <th>Código Editora</th>
            <th>Categoria do Livro</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="autor in autores" :key="autor.id">
            <td>{{autor.id}}</td>
            <td>{{autor.name}}</td>
            <td>{{autor.idadeid}}</td>
            <td>{{autor.editoracod}}</td>
            <td>{{autor.categoria}}</td>
            <td>
              <button @click="excluir(autor)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>