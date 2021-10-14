<script>
  import fetch from 'cross-fetch';
  import { onMount } from "svelte";
  let events = [];
  
  onMount(async () => {
    try 
    {
      // const res = await axios.get("https://jsonplaceholder.typicode.com/todos/1");
      //const res= await fetch("https://jsonplaceholder.typicode.com/todos/1");
      
      const params={'event-info-type':'latest-events'};
      const options={
            method: 'post',
            body: JSON.stringify(params)
      }
        const res= await fetch("/api/eventInfo",options);
  
        if (res.status >= 400) {
          throw new Error("Bad response from server");
       }
        events = await res.json();
    } 
    catch (error) 
    {
        console.log(error);
    }
  
  });
  </script>
  
  <div>
  {JSON.stringify(events)} 
  </div>
  