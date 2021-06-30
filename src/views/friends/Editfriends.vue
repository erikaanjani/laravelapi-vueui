<template>
  <div class="card shadow mt=3">
    <div class="card-body">
      <h5 class="card-title">Edit  friend</h5>
      <form class="row g-3">
        <div class="col-md-6">
          <label for="inputEmail4" class="form-label">Nama</label>
          <input type="text" class="form-control" id="inputEmail4" />
        </div>
        <div class="col-md-6">
          <label for="inputPassword4" class="form-label">No Tlp</label>
          <input type="number" class="form-control" id="inputPassword4" />
        </div>
        <div class="col-12">
          <label for="inputAddress" class="form-label">Alamat</label>
          <input
            type="text"
            class="form-control"
            id="inputAddress"
            placeholder="Masukan alamat"
          />
        </div>
      
        <div class="col-12">
          <button type="submit" class="btn btn-primary">Edit</button>
        </div>
      </form>
    </div>
  </div>
</template>
const route = useRoute();
    onMounted(()=>(
      axios.get(`http://pia.labirin.co.id/api/friends/${route.params.id}`)
      axios.get(`http://127.0.0.1:8000/api/friends/${route.params.id}`)
      .then(response => {
        console.log(response.data.data.nama)
@@ -84,7 +84,7 @@ export default {
      let no_tlp = friend.no_tlp;
      let alamat = friend.alamat;
      axios.put(`http://pia.labirin.co.id/api/friends/${route.params.id}`, {
      axios.put(`http://127.0.0.1:8000/api/friends/${route.params.id}`, {
          nama: nama,
          no_tlp: no_tlp,
          alamat: alamat,