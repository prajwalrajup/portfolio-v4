<script>
  export let skills;
  // import config from "$lib/config.json";
  import Skill from "./Skill.svelte";
  let selected;
  if (skills.length) {
    selected = skills[0];
  }
</script>

<div data-aos="fade-in" class="flex flex-col gap-10">
  {#if skills.length}
    <b class="text-xl text-highlightColor">What I Do</b>
    <div class="flex flex-col gap-4">
      {#each skills as skill (skill)}
        <button
          on:click={() => {
            selected = skill;
          }}
        >
          <Skill {skill} selected={selected == skill} />
        </button>
      {/each}
    </div>
  {/if}
</div>
