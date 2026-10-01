<script setup>
defineProps({
  busca: {
    type: String,
    required: true,
  },
  situacao: {
    type: String,
    required: true,
  },
})

const emit = defineEmits(['update:busca', 'update:situacao', 'limpar'])
</script>

<template>
  <div class="filtros">
    <input
      :value="busca"
      @input="emit('update:busca', $event.target.value)"
      type="search"
      placeholder="Buscar por título..."
      aria-label="Buscar tarefas por título"
    />

    <select
      :value="situacao"
      @change="emit('update:situacao', $event.target.value)"
      aria-label="Filtrar por situação"
    >
      <option value="todas">Todas</option>
      <option value="pendentes">Pendentes</option>
      <option value="concluidas">Concluídas</option>
    </select>

    <button type="button" @click="emit('limpar')">Limpar filtros</button>
  </div>
</template>

<style scoped>
.filtros {
  display: flex;
  gap: 8px;
  margin-bottom: 20px;
}

input,
select {
  padding: 10px 12px;
  border: 1px solid var(--border);
  border-radius: 6px;
  font-size: 14px;
  background: var(--surface);
  color: var(--text);
}

input {
  flex: 1;
}

input:focus,
select:focus {
  outline: 2px solid var(--accent);
  outline-offset: 1px;
}

button {
  padding: 10px 14px;
  border: 1px solid var(--border);
  border-radius: 6px;
  background: var(--surface);
  color: var(--text-muted);
  font-size: 14px;
  cursor: pointer;
  white-space: nowrap;
}

button:hover {
  color: var(--text);
  border-color: var(--text-muted);
}
</style>
