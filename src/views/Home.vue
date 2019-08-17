<template>
  <div>
    <div class="form-group">
      <h3 for="user">Select a user</h3>
      <select class="form-control" id="user" v-model="selectedUser">
        <option v-for="user in UsersListResponse" :key="user._id" :value="user">{{user.Name}}</option>
      </select>
    </div>

    <div class="card" style="width: 18rem;" v-if="selectedUser">
      <div class="card-body">
        <h5 class="card-title">{{selectedUser.Name}}</h5>
        <h6 class="card-subtitle mb-2 text-muted">{{selectedUser.Gender}}</h6>
        <p class="card-text">Age: {{selectedUser.Age}}</p>
      </div>
      <div class="card-footer">
         <span class="badge badge-pill badge-danger mr-1" v-for="preference in selectedUser.Preferences" :key="preference">{{preference}}</span>
      </div>
    </div>
    
    <div v-if="selectedUser">
      <h3 class="mt-5">Offers</h3>
      <div class="card-columns">
        <div class="card" v-for="offer in UserOffersResponse[0].Offers" :key="offer._id">
          <div class="card-body">
            <h5 class="card-title">{{offer.OfferTitle}}</h5>
            <h6 class="card-subtitle mb-2 text-muted">{{offer.OfferTag}}</h6>
            <button type="button" class="btn btn-primary">Like</button>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
// import axios from 'axios'
import OfferDetailResponse from '@/json/OfferDetailResponse.json'
import UserOffersResponse from '@/json/UserOffersResponse.json'
import UsersListResponse from '@/json/UsersListResponse.json'
import UserUpdateOfferInfoRequest from '@/json/UserUpdateOfferInfoRequest.json'

export default {
  name: 'home',
  data () {
    return {
      selectedUser: '',
      OfferDetailResponse: OfferDetailResponse,
      UserOffersResponse: UserOffersResponse,
      UsersListResponse: UsersListResponse,
      UserUpdateOfferInfoRequest: UserUpdateOfferInfoRequest
    }
  },
  components: {},
  created () {
    // axios.get('/OfferDetailResponse.json')
    //   .then((res) => {
    //     console.log(res.data)
    //   }).catch((err) => {
    //     console.log(err)
    //   })
  }
}
</script>
