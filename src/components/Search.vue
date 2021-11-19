<template>
  <div class="row">
    <div class="col-md-4 search_manager">
      <div class="row">
        <div class="col">
          <div class="search_header">
            <div class="col-md-11">
              <router-link to="" class="back_link"
                ><i class="fas fa-arrow-alt-circle-left"></i
                ><span class="back">Back</span></router-link
              >
              <span class="search_title">Search Manager</span>
            </div>
            <div class="arrow col-md-1">
              <i class="fas fa-chevron-circle-left" style="font-size: 24px"></i>
            </div>
          </div>
          <div class="search_action">
            <div class="col">
              <span class="s_action btn">
                <i class="fas fa-search mr-2"></i> save search</span
              >
              <span class="s_action btn"
                ><i class="fas fa-redo mr-2"></i> load search result</span
              >
            </div>
          </div>

          <div class="range row">
            <div class="col range_col">
              <label
                for="customRange1"
                class="form-label labelage"
                style="color: #675aaa"
                >Age</label
              >
              <i
                class="fas fa-minus-circle btn"
                @click="minage"
                style="font-size: 24px; color: #8b83c6; margin-left: 45px"
              ></i>
              <input
                type="range"
                class="col-sm-6 slider"
                value="27"
                @click="getAge"
                v-model="age"
                min="27"
                max="100"
                data-step="1"
                data-value="128"
                data-id="RC"
                id="R"
                data-tooltip="hide"
                data-handle="square"
              />
              <i
                class="fas fa-plus-circle btn"
                @click="maxage"
                style="font-size: 24px; color: #8b83c6; margin-left: 155px"
              ></i>
            </div>
            <div class="showAge">
              <span v-show="agenotClick">27 - 27 years old</span>

              <span v-show="!agenotClick">27 - {{ age }} years old</span>
            </div>
          </div>
          <div class="heightrange row">
            <div class="col heightrange_col">
              <div>
                <i
                  @click.prevent="incrementFeet"
                  class="fas fa-chevron-circle-up btn"
                  style="font-size: 30px; color: #8b83c6; margin-right: 30px"
                ></i>
                <i
                  class="fas fa-chevron-circle-up btn"
                  style="font-size: 30px; color: #8b83c6; margin-right: -10px"
                  @click="incrementInch"
                ></i>
              </div>
              <div class="row height_details">
                <div class="col-md-4 col4">
                  <label
                    for="customRange1"
                    class="form-label"
                    style="color: #675aaa"
                    ><span style="margin-left: 10px">Height</span>
                  </label>
                </div>
                <div class="col-md-8 col8">
                  <span style="margin-left: 20px; float: left"
                    >{{ feet }} ft</span
                  ><span style="float: right; position: absolute; left: 75px"
                    >.</span
                  ><span style="float: right; position: absolute; left: 125px"
                    >{{ inch }} inch</span
                  >
                </div>
              </div>
              <div>
                <i
                  class="fas fa-chevron-circle-down btn"
                  @click.prevent="decrementFeet"
                  style="
                    font-size: 30px;
                    color: #8b83c6;
                    position: relative;
                    right: 13px;
                  "
                ></i
                ><i
                  class="fas fa-chevron-circle-down btn"
                  style="
                    font-size: 30px;
                    color: #8b83c6;
                    margin-rgiht: -10px;
                    position: relative;
                    left: 25px;
                  "
                  @click="decrementInch"
                ></i>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="row option1 mt-5 mb-3">
        <div class="optionbox">
          <label for="" class="spansty">Religion</label>
          <select
            v-model="rel"
            @click="pasrel(rel)"
            class="form-select"
            style="border: none"
            aria-label="Default select example"
          >
            <option
              :value="religion.id"
              v-for="religion in religions"
              :key="religion.id"
            >
              {{ religion.name }}
            </option>
          </select>
        </div>
      </div>
      <div class="row option2 mb-3">
        <div class="optionbox">
          <label for="" class="spansty">Country</label>
          <select
            class="form-select"
            style="border: none"
            aria-label="Default select example"
            v-model="country"
            @click="pascou(country)"
          >
            <option selected>Country</option>
            <option
              :value="Country.id"
              v-for="Country in countries"
              :key="Country.id"
            >
              {{ Country.name }}
            </option>
          </select>
        </div>
      </div>
      <div class="row option3 mb-3">
        <div class="optionbox">
          <label for="" class="spansty">Gender</label>

          <select
            class="form-select"
            style="border: none"
            aria-label="Default select example"
            v-model="gender"
            @click="pasgen(gender)"
          >
            <option selected>Gender</option>
            <option
              :value="gender.id"
              v-for="gender in genders"
              :key="gender.id"
            >
              {{ gender.name }}
            </option>
          </select>
        </div>
      </div>
      <div class="row option4 mb-3">
        <div class="optionbox">
          <label for="" class="spansty">Marriage Status</label>

          <select
            class="form-select"
            style="border: none"
            aria-label="Default select example"
            v-model="status"
            @click="passta(status)"
          >
            <option selected>Maritial Status</option>
            <option
              :value="status.id"
              v-for="status in marriageStatus"
              :key="status.id"
            >
              {{ status.name }}
            </option>
          </select>
        </div>
      </div>
      <div class="row option5 mb-3">
        <div class="optionbox">
          <label for="">Tags</label>
          <textarea
            class="form-control"
            name=""
            id=""
            cols="35"
            rows="5"
            style="border: 1px solid #675aaa"
          ></textarea>
          <span class="s_action btn mt-3" style="width: 170px">
            <i class="fas fa-search mr-2"></i> save search</span
          >
          <span
            class="btn mt-2"
            style="width: 170px; color: #675aaa; text-decoration: underline"
          >
            Advance search</span
          >
        </div>
      </div>
    </div>
    <div class="col-md-8 list_manager">
      <div class="row firstrow">
        <div class="col-md-4">
          <h2 style="color: #838080">Search Result</h2>
        </div>

        <div class="col-md-4">
          <span class="adsearch btn"
            ><i class="fas fa-align-left"></i> Manage Filters</span
          >
        </div>
        <div class="col-md-4">
          <span class="adsearch btn"
            ><i class="fas fa-search mr-2"></i> Advance search</span
          >
        </div>
        <div>
          <div class="row secondrow">
            <div class="col-md-4" style="width: 200px; margin-right: 130px">
              <i
                class="fas fa-border-all"
                style="font-size: 35px; color: #675aaa; margin-right: 20px"
              ></i
              ><i
                class="fas fa-align-right"
                style="
                  font-size: 35px;
                  background: #675aaa;
                  color: white;
                  padding: 2px;
                "
              ></i>
            </div>

            <div class="col-md-8 btngroup isgrp" style="width: 600px">
              <span class="btn info"> Age: {{ age }}</span>
              <span class="btn info" style="font-size: 14px">
                {{ feet }} feet {{ inch }} inch</span
              >
              <span class="btn info" v-if="showrel"> {{ rel }}</span>
              <span class="btn info" v-if="showcou"> {{ country }}</span>
              <span class="btn info" v-if="showgen"> {{ gender }}</span>
              <span class="btn info" v-if="showsta"> {{ status }}</span>
            </div>
          </div>
          <div class="row thirdrow">
            <div class="col">
              <div class="list">
                <ul>
                  <li
                    v-for="pro in profile"
                    :key="pro.id"
                    style="list-style: none; margin-bottom: 5px"
                  >
                    <img
                      :src="require('../assets/img/' + pro.image)"
                      style="width: 80px; height: 80px"
                      alt=""
                    />

                    <span
                      style="
                        font-size: 25px;
                        position: absolute;
                        margin-left: 5px;
                      "
                    >
                      {{ pro.name }}
                    </span>
                    <span
                      style="
                        margin-top: 40px;
                        position: absolute;
                        margin-left: 8px;
                      "
                    >
                      {{ pro.country }} </span
                    ><span
                      style="position: absolute; left: 262px; padding-top: 40px"
                      >{{ pro.age }} years</span
                    >
                    
                        <span class="btn over "><i class="fas fa-star"></i>Short List </span>
                      <span class="btn  " style='background: #8b83c6;color:white'> <i class="fas fa-star" style='margin-left:5px;'></i> Team List</span>
                      <span class="btn " style='background: #8b83c6;color:white'> <i class="fas fa-network-wired" style='margin-left:5px;'></i> Connect </span>
                      <span class="btn " style='background:#ef217b;color:white'><i class="fas fa-ban" ></i> Block</span>
                    
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "Search",

  data() {
    return {
      age: "",
      agenotClick: true,
      initialFeet: true,
      initialInch: true,
      feet: 4,
      inch: 0,
      rel: "",
      country: "",
      gender: "",
      status: "",
      showrel: false,
      showsta: false,
      showcou: false,
      showgen: false,
      religions: [
        { id: 1, name: "Islam" },
        { id: 2, name: "Hindu" },
        { id: 3, name: "Christian" },
        { id: 4, name: "Buddhism" },
      ],
      countries: [
        { id: 1, name: "Bangladesh" },
        { id: 2, name: "India" },
        { id: 3, name: "Pakistan" },
        { id: 4, name: "Nepal" },
      ],
      genders: [
        { id: 1, name: "Male" },
        { id: 2, name: "Female" },
        { id: 3, name: "Others" },
      ],
      marriageStatus: [
        { id: 1, name: "Married" },
        { id: 2, name: "Single" },
      ],
      profile: [
        {
          id: 1,
          name: "Enamul",
          age: 25,
          country: "Bangladesh",
          image: "img.jpg",
        },
        {
          id: 2,
          name: "Enamul",
          age: 25,
          country: "Bangladesh",
          image: "img.jpg",
        },
        {
          id: 3,
          name: "Enamul",
          age: 25,
          country: "Bangladesh",
          image: "img.jpg",
        },
        {
          id: 4,
          name: "Enamul",
          age: 25,
          country: "Bangladesh",
          image: "img.jpg",
        },
        {
          id: 5,
          name: "Enamul",
          age: 25,
          country: "Bangladesh",
          image: "img.jpg",
        },
        {
          id: 6,
          name: "Enamul",
          age: 25,
          country: "Bangladesh",
          image: "img.jpg",
        },
      ],
    };
  },
  methods: {
    getAge() {
      this.agenotClick = !this.agenotClick;
      console.log(this.age);
      this.$emit("action", localStorage.setItem("age", this.age));
    },
    minage() {
      this.age = "27";
      this.agenotClick = true;
    },
    maxage() {
      this.agenotClick = false;
      this.age = "100";
    },
    incrementFeet() {
      if (this.feet < 6) {
        this.feet = this.feet + 1;
        console.log(this.feet);
      }
    },
    decrementFeet() {
      if (this.feet > 4) {
        this.feet = this.feet - 1;
        console.log(this.feet);
      }
    },

    incrementInch() {
      if (this.inch < 12) {
        this.inch += 1;
        console.log(this.inch);
      }
    },
    decrementInch() {
      if (this.inch > 0) {
        this.inch = this.inch - 1;
      }
    },
    pasrel(id) {
      this.showrel = true;
      this.religions.map((item) => {
        if (item.id == id) {
          this.rel = item.name;
        }
      });
    },
    pascou(id) {
      this.showcou = true;

      this.countries.map((item) => {
        if (item.id == id) {
          this.country = item.name;
        }
      });
    },
    pasgen(id) {
      this.showgen = true;

      this.genders.map((item) => {
        if (item.id == id) {
          this.gender = item.name;
        }
      });
    },
    passta(id) {
      this.showsta = true;
      this.marriageStatus.map((item) => {
        if (item.id == id) {
          this.status = item.name;
        }
      });
    },
  },
};
</script>
<style>
.search_manager {
  display: flex;
  flex-direction: column;
  height: 100%;
  width: 350px;
  height: 800px;
  margin-bottom:200px;
}
.search_header {
  background: #675aaa;
  height: 50px;
  border-top-left-radius: 147px;
  color: white;
  border-bottom-right-radius: 134px;
  display: flex;
}
.back {
  margin-left: 5px;
}

.back_link {
  background: white;
  color: #675aaa;
  display: inline-block;
}
.height_details {
  display: flex;
  color: #675aaa;
}
.search_header .back_link {
  margin-top: 8px;
  float: left;
  margin-left: 50px;
  padding: 5px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
}
.search_header .back_link:hover {
  text-decoration: none;
  background: white;
  color: #675aaa;
}
.search_title {
  float: left;
  margin-left: 40px;
  margin-top: 10px;
  font-size: 18px;
}
.search_action {
  display: flex;
  margin-top: 10px;
  top: 65px;
}
.col4 {
  position: absolute;
  /* float: left; */
  width: 40px;
}
.col8 {
  position: relative;
  display: inline-block;
  /* margin-left: 30px; */
  left: 75px;
  width: 257px;
  font-size: 25px;
}
.s_action {
  background: rgb(103, 90, 170);
  color: white;
  padding: 10px;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
}
.s_action:hover {
  color: #dbe2eb;
}
.spansty {
  margin-bottom: 3px;
  color: #625aad;
}
.arrow {
  background: rgb(103, 90, 170);
  border: 1px solid white;
  border-top-left-radius: 45px;
  border-bottom-left-radius: 46px;
  margin-top: 5px;
  width: 35px;
}
.arrow i {
  margin-top: 10px;
  margin-left: 6px;
  display: inline-block;
}
.range {
  margin-top: 20px;
  position: relative;
  width: 350px;
}
.heightrange {
  top: 197px;
  width: 320px;
  left: 70px;
}

.heightrange_col {
  float: left;
  display: inline-block;
}
.range_col {
  float: left;
  display: inline-flex;
}
.optionbox {
  border-top-left-radius: 15px;
  border-bottom-left-radius: 15px;
  border-top-right-radius: 15px;
  border-bottom-right-radius: 15px;
}

.slider {
  -webkit-appearance: none;
  width: 150px;
  height: 20px;
  background: #8b83c6;
  outline: none;
  border: 5px solid #f4f9f0;
  border-radius: 8px;
  position: absolute;
  top: 8px;
  margin-left: 100px;
}
.labelage {
  left: 30px;
  position: absolute;
  top: 5px;
}
.option1 {
  position: relative;
  left: 20px;
  width: 300px;
}
.option2 {
  position: relative;
  left: 20px;
  width: 300px;
}
.option3 {
  position: relative;
  left: 20px;
  width: 300px;
}
.option4 {
  position: relative;
  left: 20px;
  width: 300px;
}
.option5 {
  position: relative;
  left: 20px;
  width: 300px;
}
.form-select {
  color: #675aaa;
}
/* for chrome/safari */
.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 25px;
  height: 25px;
  background: #625aad;
  cursor: pointer;

  border-radius: 4px;
}

/* for firefox */
.slider::-moz-range-thumb {
  width: 20px;
  height: 60px;
  background: #000;
  cursor: pointer;
  border: 5px solid lawngreen;
  border-radius: 4px;
}
.showAge {
  color: #625aad;
  position: relative;
  left: 0;
}
.adsearch {
  background: rgb(103, 90, 170);
  color: white;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
  border-bottom-left-radius: 20px;
  border-bottom-right-radius: 20px;
  padding-top: 7px;
  float: right;
  height: 40px;
  width: 175px;
}
.adsearch:hover {
  color: white;
}
.secondrow {
  position: absolute;
  top: 100px;
}
.thirdrow {
  position: absolute;
  top: 200px;
  margin-left: 40px;
}
.btngroup {
  display: flex;
}
.info {
  width: 115px;
  background: #8b83c6;
  margin-left: 5px;
  height: 30px;
  color: white;
}
.info:hover {
  color: white;
}
.over{
   background: #8b83c6;
  margin-left: 5px;
  height: 30px;
  color: white;
  margin-left:200px;
  height:35px;
}
.list_manager{
  width:845px;
  top:0;
  left:0;
  right:0;
position:relative;
}
.isgrp{
  width: 600px;
    display: inline;
    /* margin-bottom: -9px; */
    position: relative;
    top: -40px;
}
</style>