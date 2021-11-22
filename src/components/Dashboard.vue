<template>
  <div id="burger_table">
    <div>
      <div id="burger_table_header">
        <div class="order_id">#:</div>
        <div>Cliente: </div>
        <div>Pão: </div>
        <div>Carne: </div>
        <div>Opcionais: </div>
        <div>Ações: </div>
      </div>
      <div id="burger_table_rows">
        <div class="burger_table_row">
          <div class="order_number">1</div>
          <div>João</div>
          <div>Pão de trigo</div>
          <div>Maminha</div>
          <div>
            <ul>
              <li>Salame</li>
              <li>Tomate</li>
            </ul>
          </div>
          <div>
            <select name="status" class="status">
              <option value="">Selecione</option>
            </select>
            <button class="delete_btn">Cancelar</button>
          </div>
        </div>
        <div class="burger_table_row">
          <div class="order_number">1</div>
          <div>João</div>
          <div>Pão de trigo</div>
          <div>Maminha</div>
          <div>
            <ul>
              <li>Salame</li>
              <li>Tomate</li>
            </ul>
          </div>
          <div>
            <select name="status" class="status">
              <option value="">Selecione</option>
            </select>
            <button class="delete_btn">Cancelar</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dashboard"
}
</script>

<style scoped>
  #burger_table {
    max-width: 1200px;
    margin: 0 auto;
  }

  #burger_table_header,
  #burger_table_rows,
  .burger_table_row {
    display: flex;
    flex-wrap: wrap;
  }

  #burger_table_header {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333333;
  }

  #burger_table_header div,
   .burger_table_row div {
    width: 19%;
  }

  .burger_table_row {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #ccc;
  }

  #burger_table_header .order_id,
  .burger_table_row .order_number {
    width: 5%;
  }

  select {
    padding: 12px 6px;
    margin-right: 12px;
  }

  .delete_btn {
    background-color: #222222;
    color: #fcba03;
    font-weight: bold;
    border: 2px solid #222222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;

    transition: .5s;
  }

  .delete_btn:hover {
    background-color: transparent;
    color: #222222;
  }


















</style>