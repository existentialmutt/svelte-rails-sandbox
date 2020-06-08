<script>
  import {votes} from "./store.js"
  import cloneDeep from "lodash/cloneDeep"

  export let choiceKey
  export let label
  export let avatarSrc

  function handleVote() {
    votes.update(oldVotes => {
      const newVotes = cloneDeep(oldVotes)
      newVotes[choiceKey] || (newVotes[choiceKey] = 0)
      newVotes[choiceKey]++
      return newVotes
    })
  }
</script>

<style>
  .wrapper {
    display: flex;
    margin-bottom: 10px;
    align-items: center;
    padding: 12px 24px;
    border-radius: 4px;
    border: solid 1px #808080;
    cursor: pointer;
  }
  .avatar {
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin-right: 10px;
  }
</style>


<div class="wrapper" on:click|preventDefault={handleVote}>
  <img class="avatar" src={avatarSrc} alt="a picture of {choiceKey}" />
  {label}
</div>