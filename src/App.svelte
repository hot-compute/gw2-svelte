<script>
  import { onMount } from "svelte";
  import { apiData, achievementIds, achievementsData, achievements } from './store.js';
  
  let dailyIds = "2957,1969";
  
  onMount(async () => {
    fetch("https://api.guildwars2.com/v2/achievements/daily")
    .then(response => response.json())
    .then(data => {
      console.log(data);
      apiData.set(data);
    }).catch(error => {
      console.log(error);
      return [];
    });
    
    fetch("https://api.guildwars2.com/v2/achievements?ids=" + dailyIds)
    .then(response => response.json())
    .then(data => {
      console.log(data);
      achievementsData.set(data);
    }).catch(error => {
      console.log(error);
      return [];
    });
  });
  </script>
  
  <main>
    <h1>Guild Wars 2 Achievements Daily</h1>
    <h2>List of Daily ID's</h2>
    <ul>
    {#each $achievementIds as achievementId}
      <li><a href="https://api.guildwars2.com/v2/achievements?ids={achievementId}">{achievementId}</a></li>
    {/each}
  </ul>
  
  <h2>List of Achievements by ID</h2>
  <ul>
  {#each $achievements as achievement}
    <li>{achievement}</li>
  {/each}
  </ul>

  <h2>Festival's</h2>
  <p>Check out this <a href="https://guildjen.com/2021/12/14/wintersday-festival-achievements-guide/?fbclid=IwAR37Npe0TcBhkgqxTy8S2f1Gs7hSBGCGQS5N_XVMxlIGAWwyQgeUxkDp9Tk">Winter's Day Achievement Guide!</a></p>
  
</main>
  
  <style>
  
  </style>