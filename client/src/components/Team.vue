<template>
  <div class="team">
      <div v-if="users.length > 0" class="team-members table">
          <div class="table-header table-row">
            <div class="table-col">Name</div>
            <div class="table-col">E-mail</div>
            <div class="table-col table-actions">Actions</div>
          </div>
          <div v-for="user in users" :key="user.id" class="member table-row">
            <div class="table-col name">{{ user.name }}</div>
            <div class="table-col email">{{ user.email }}</div>
            <div class="table-col actions">
                <div class="button-group group-end">
                    <button class="button button-small" @click="() => toggleForm(user.id)">Update</button>
                    <button class="button button-small button-alert" @click="() => deleteUser(user.id)">Delete</button>
                </div>
            </div>
          </div>
      </div>
      <div v-else class="no-team">No member yet</div>
  </div>
</template>

<script>
import APIController from '../controllers/api';

export default {
    props: ["users", "toggleForm", "fetchUsers"],
    setup(props) {
        const deleteUser = async(id) => {
            const success = await APIController.DeleteUser(id);

            if(success) {
                props.fetchUsers();
            }
        }

        return { deleteUser }
    }
}
</script>

<style>
.team {
    padding: 16px;
}

.table-row {
    display: flex;
    align-items: center;
}

.table-col {
    flex: 1 1 33.333%;
    padding: 16px;
    color: var(--grey);
}

.table-row {
    background-color: #FFF;
}

.table-row:nth-child(2n+1) {
    background-color: var(--light-alt);
}

.table .table-header {
    background-color:  var(--dark);
}

.table .table-header .table-col {
    color: var(--light);
}
.table-actions {
    text-align: right;
}
</style>