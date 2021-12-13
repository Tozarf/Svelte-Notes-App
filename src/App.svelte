<script>
  import Header from "./components/Header.svelte";
  import DashBoard from "./components/Dashboard.svelte";
  import { v4 } from "uuid";

  let notes = [
    {
      id: 0,
      title: "Vacations",
      color: "#FFC2D8",
      text: "Sup!",
    },
    {
      id: 1,
      title: "Vacations",
      color: "#FFC2C2",
      text: "Sup!",
    },
  ];

  let copyNotes = [...notes];
  $: count = notes.length;

  function handleNewNote() {
    const color = generateColor();
    const id = v4();
    const note = {
      id: id,
      title: "",
      color: color,
      text: "",
    };
    notes = [note, ...notes];
    copyNotes = [...notes];
  }

  function generateColor() {
    const colors = ["#DDFC2", "#FFC2C2", "#FFEAC2", "#C2FFD3", "#C2FFEC", "#C2FAFF", "#C2E2FF", "#CBC2FF", "#EBC2FF", "#FFCF7", "#FFC2D8"];
    const index = Math.floor(Math.random() * colors.length);
    return colors[index];
  }
</script>

<main>
  <Header />
  <div class="count-notes">{count} notas</div>
  <DashBoard {notes} on:click={handleNewNote} />
</main>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
  }
  .count-notes {
    padding: 20px 20px 0 20px;
    text-align: right;
  }
</style>
