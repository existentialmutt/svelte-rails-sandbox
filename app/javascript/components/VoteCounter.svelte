<script>
  import {votes} from "./store.js"

  export let choiceKey
  export let label
  export let avatarSrc

  let voteCount
  const unsubscribeVotes = votes.subscribe(votesValue => {
    voteCount = (votesValue[choiceKey] || 0)
  })
</script>

<style>
  .wrapper {
    display: flex;
    margin-bottom: 10px;
    align-items: center;
  }

  .avatar {
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin-right: 10px;
  }
</style>

<div class="wrapper">
  <img class="avatar" src={avatarSrc} alt="a picture of {choiceKey}" />
  <div class="label">{label}: {voteCount}</div>
</div>