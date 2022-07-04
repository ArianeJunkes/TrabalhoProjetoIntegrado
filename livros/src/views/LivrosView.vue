<script>
import { v4 as uuid} from "uuid";
export default {
  data() {
    return {
      novo_livro: "",
      novo_preco: "",
      novo_editora: "",
      novo_categoria: "",
      novo_autor: "",
      livros: [
        { id: "9a7c7c02-874d-4556-8a13-4a33c56571d1", name: "A Família de Marcelo", precoid: "36,20", editoracod:"1", categoria:"Junvenil", autor:"Ruth Rocha"},
        { id: "475f6d39-5a56-4442-8a2d-5ceba6b4b807", name: "A Seleção", precoid: "28,89", editoracod:"2", categoria:"Romance", autor:"Kiera Cass"},
        { id: "874b37b6-3546-4c05-bc54-5d0fdb886d16", name: "A herança de uma nobre mulher", precoid: "23,90", editoracod:"3", categoria:"Romance", autor:"Danielle Steel"},
        { id: "9b35ce67-a4ec-45a0-be67-1983e37bd723", name: "É Assim Que Acaba", precoid: "34,90", editoracod:"4", categoria:"Romance", autor:"Colleen Hoover"},
      ],
    };
  },
  methods: {
    salvar() {
      if (this.novo_livro !== ""){
      const novo_id=uuid();
      this.livros.push({
        id: novo_id,
        name: this.novo_livro,
        precoid: this.novo_preco,
        editoracod: this.novo_editora,
        categoria: this.novo_categoria,
        autor: this.novo_autor,
      });
        this.novo_livro = "";
        this.novo_preco = "";
        this.novo_editora = "";
        this.novo_categoria = "";
        this.novo_autor = "";
      }
    },
    excluir(livro){
      const indice = this.livros.indexOf(livro);
      this.livros.splice(indice, 1);
    },
  },
};
</script>
<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de livros</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Nome" v-model="novo_livro" @keypress.enter="salvar" />
      <input type="text" placeholder="Preço" v-model="novo_preco" @keypress.enter="salvar" />
      <input type="text" placeholder="Código Editora" v-model="novo_editora" @keypress.enter="salvar" />
      <input type="text" placeholder="Gênero" v-model="novo_categoria" @keypress.enter="salvar" />
      <input type="text" placeholder="Nome Autor" v-model="novo_autor" @keypress.enter="salvar" />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-items">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>R$</th>
            <th>Código Editora</th>
            <th>Categoria do Livro</th>
            <th>Autor</th>
            <th>Ação</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{livro.id}}</td>
            <td>{{livro.name}}</td>
            <td>{{livro.precoid}}</td>
            <td>{{livro.editoracod}}</td>
            <td>{{livro.categoria}}</td>
            <td>{{livro.autor}}</td>
            <td>
              <button @click="excluir(livro)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<style></style>
