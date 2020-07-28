<script>
  import { onMount } from "svelte";
  import currency from "currency.js";
  import Button from "./Button.svelte";

  let cars = [];

  const rub = (value) =>
    currency(value, {
      symbol: "₽",
      separator: " ",
      precision: 0,
    });

  onMount(async () => {
    const res = await fetch(
      `https://rawgit.com/Varinetz/e6cbadec972e76a340c41a65fcc2a6b3/raw/90191826a3bac2ff0761040ed1d95c59f14eaf26/frontend_test_table.json`
    );
    cars = await res.json();
  });
</script>

<style>
  .table {
    background-color: #f5f6f6;
  }
  header {
    display: none;
  }
  section {
    display: flex;
    flex-wrap: wrap;
    padding: 0 0.5rem;
    justify-content: space-between;
    border-top: 1px #e6e9ea solid;
  }
  .table div {
    padding: 1rem 0.5rem;
  }
  .name {
    order: 1;
    width: 50%;
    flex: 1 1 auto;
  }
  .color {
    order: 2;
    flex: 1;
    text-align: center;
  }
  .price {
    order: 3;
    flex: 1;
    white-space: nowrap;
  }
  .description {
    width: 100%;
    order: 4;
    opacity: 0.6;
    padding: 0;
  }
  .year {
    order: 5;
  }
  .status {
    order: 6;
    white-space: nowrap;
  }
  .action {
    order: 7;
    text-align: right;
  }
  section + div.description {
    display: none;
  }
  span {
    width: 1.25rem;
    height: 1.25rem;
    display: inline-block;
    border-radius: 100%;
    border: 1px #ddd solid;
  }
  span.red {
    background-color: red;
  }
  span.black {
    background-color: black;
  }

  span.white {
    background-color: white;
  }
  span.green {
    background-color: green;
  }
  @media screen and (min-width: 45em) {
    .table {
      display: table;
      width: 100%;
      border-radius: 0.25rem;
      border-collapse: collapse;
      overflow: hidden;
    }
    .table div {
      display: table-cell;
      vertical-align: middle;
      padding: 0.5rem 1rem;
    }

    header {
      color: #fff;
      font-weight: medium;
      background-color: #c4092f;
    }
    section,
    header {
      display: table-row;
    }

    /* Hack */
    section div.description {
      display: none;
    }
    section + div.description {
      display: block;
      top: -0.5rem;
      position: relative;
    }
  }
</style>

<div class="table">
  <header>
    <div class="name">Название</div>
    <div class="year">Год</div>
    <div class="color">Цвет</div>
    <div class="status">Статус</div>
    <div class="price">Цена</div>
    <div class="action" />
  </header>

  {#each cars as car}
    <section>
      <div class="name">{car.title}</div>
      {#if car.description}
        <div class="description">{car.description}</div>
      {/if}
      <div class="year">{car.year}</div>
      <div class="color">
        <span class={car.color} aria-label={car.color} />
      </div>
      <div class="status">
        {#if car.status === 'out_of_stock'}
          Нет в наличии
        {:else if car.status === 'pending'}Ожидается{:else}В наличии{/if}
      </div>
      <div class="price">{rub(car.price).format()}</div>
      <div class="action">
        <Button type="submit">Удалить</Button>
      </div>
    </section>
    <!-- For Desktop View -->
    {#if car.description}
      <div class="description">{car.description}</div>
    {/if}
  {/each}
</div>
