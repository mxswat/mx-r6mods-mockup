<template>
  <div class="modmain">
    <div class="players">
      <template v-for="(player, i) in players">
        <label class="player-label" :for="player" v-bind:key="player">
          <input
            class="radio-hide"
            type="radio"
            :id="player"
            name="player-name"
            :value="player"
            :checked="i == 0"
          />
          <span class="player-name">{{player}}</span>
        </label>
      </template>
    </div>
    <div class="selection-columns">
      <div class="weapons">
        <span class="weapons-tile">WEAPONS</span>
        <NestedList :source="weapons"></NestedList>
      </div>
    </div>
  </div>
</template>

<script>
import weapons from "../weapons";
import NestedList from "./NestedList";
export default {
  name: "ModMain",
  props: {
    msg: String
  },
  components: {
    NestedList
  },
  data: () => {
    return {
      isOpenWeaponCat: {},
      weapons: null,
      players: [
        "Player 1",
        "Player 2",
        "Player 3",
        "Player 4",
        "Player 5",
        "Player 6",
        "Player 7",
        "Player 8",
        "Player 9",
        "Player 10",
        "Everyone"
      ]
    };
  },
  created() {
    this.weapons = weapons;
  },
};
</script>

<style lang="scss">
$primary: #2196f3;
$primary50: rgba(33, 149, 243, 0.5);
$secondary: #ff5722;

.players {
  text-align: center;
  padding-bottom: 20px;
  border-bottom: 1px solid gray;
}
:checked + span.player-name {
  color: #ff5722;
  padding-bottom: 12px;
  border-bottom: 2px solid $secondary;
}

.player-name {
  padding: 12px;
  padding-bottom: 14px;
  margin: 0px 8px;
  cursor: pointer;
  font-weight: bold;
  text-transform: uppercase;
  &:hover {
    background: $primary50;
  }
}

.selection-columns {
  max-width: 1024px;
  margin: auto;
  margin-top: 20px;
  display: grid;
  display: grid;
  grid-template-columns: repeat(2, [col] 1fr);
  grid-template-rows: repeat(2, [row] auto);
  gap: 8px;
}

.radio-hide {
  display: none;
}

.weapons,
.utility {
  outline: 1px solid gray;
  padding: 16px;
  max-height: 600px;
  overflow: auto;
}

</style>
