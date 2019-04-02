<template>
  <v-card flat>
    <v-container fluid grid-list-md grey lighten-4>
      <v-layout row wrap>
        <v-flex xs12 md6>
          <SelectItem
            :handelSelectChange="handelCategorySelectChange"
            :items="categories"
            :selectedItem="selectedCategory"
            :icon="'category'"
            :label="'Category'"
          />
        </v-flex>
        <v-flex xs12 md6>
          <v-text-field label="Title" v-model="announcement.title" :append-icon="'title'"></v-text-field>
        </v-flex>
      </v-layout>
      <v-layout row wrap>
        <v-flex xs12 md4 v-if="parsedId === 2">
          <SelectItem
            :handelSelectChange="handelMarkSelectChange"
            :items="marks"
            :selectedItem="selectedMark"
            :label="'Mark'"
          />
        </v-flex>
        <v-flex
          xs12
          md4
          v-if="selectedMark && selectedMark.id"
        >
          <SelectItem
            :handelSelectChange="handelModelSelectChange"
            :items="selectedMark.models"
            :selectedItem="selectedModel"
            :label="'Model'"
          />
        </v-flex>
        <v-flex xs12 md4 v-if="this.parsedId === 2">
          <SelectItem
            :handelSelectChange="handelYearSelectChange"
            :items="years"
            :selectedItem="selectedYear"
            :label="'Year of model'"
          />
        </v-flex>
        <v-flex xs12 md4 v-if="this.parsedId > 1 && this.parsedId < 6">
          <SelectItem
            :handelSelectChange="handelTypeOfFuelSelectChange"
            :items="typeOfFuels"
            :selectedItem="selectedTypeOfFuel"
            :label="'Type of fuel'"
          />
        </v-flex>
        <v-flex xs12 md4 v-if="this.parsedId === 2">
          <SelectItem
            :handelSelectChange="handelTypeOfGearBoxSelectChange"
            :items="typeOfGearBox"
            :selectedItem="selectedTypeOfGearBox"
            :label="'Type of fear box'"
          />
        </v-flex>
        <v-flex xs12 md4 v-if="this.parsedId > 1 && this.parsedId < 6">
          <v-text-field label="Mileage" v-model="announcement.mileage" :append-icon="'M'"></v-text-field>
        </v-flex>
        <v-flex xs12 md4 v-if="this.parsedId ===3">
          <v-text-field label="Cylinder" v-model="announcement.cylinderVolume" :append-icon="'C'"></v-text-field>
        </v-flex>
      </v-layout>
    </v-container>
  </v-card>
</template>

<script lang="ts">
import SelectItem from "../../components/SelectItem.vue";
import { Component, Vue } from "nuxt-property-decorator";

@Component({
  components: {
    SelectItem
  }
})
export default class Add extends Vue {
  public parsedId: number = 0;
  public selectedMark: any = {};
  public selectedCategory: any = { id: "1", label: "Job offers" };
  public selectedModel: any = {};
  public selectedYear: any = {};
  public typeOfFuels: any[] = [
    { id: "1", label: "Diesel" },
    { id: "2", label: "Electric" },
    { id: "3", label: "Gasoline" }
  ];
  public typeOfGearBox: any[] = [
    { id: "1", label: "Manual" },
    { id: "2", label: "Automatic" }
  ];
  public selectedTypeOfGearBox: any = {};
  public selectedTypeOfFuel: any = {};
  public marks = [
    {
      id: "1",
      label: "Audi",
      shortName: "audi",
      models: [
        { id: "1", label: "100" },
        { id: "2", label: "200" },
        { id: "3", label: "80" },
        { id: "4", label: "A" },
        { id: "5", label: "A1" },
        { id: "6", label: "A2" },
        { id: "7", label: "A3" },
        { id: "8", label: "A4" },
        { id: "9", label: "A4 ALLROAD" },
        { id: "10", label: "A5" },
        { id: "11", label: "A6" },
        { id: "12", label: "A6 ALLROAD" },
        { id: "13", label: "A7" },
        { id: "14", label: "A8" },
        { id: "15", label: "ALLROAD" },
        { id: "16", label: "COUPE" },
        { id: "17", label: "COUPE GT" },
        { id: "18", label: "Q2" },
        { id: "19", label: "Q3" },
        { id: "20", label: "Q5" },
        { id: "21", label: "Q7" },
        { id: "22", label: "Q8" },
        { id: "23", label: "QUATTRO" },
        { id: "24", label: "R8" },
        { id: "25", label: "RS Q3" },
        { id: "26", label: "RS2" },
        { id: "27", label: "RS3" },
        { id: "28", label: "RS4" },
        { id: "29", label: "RS5" },
        { id: "30", label: "RS6" },
        { id: "31", label: "RS7" },
        { id: "32", label: "S1" },
        { id: "33", label: "S3" },
        { id: "34", label: "S4" },
        { id: "35", label: "S5" },
        { id: "36", label: "S6" },
        { id: "37", label: "S7" },
        { id: "38", label: "S8" },
        { id: "39", label: "SQ5" },
        { id: "40", label: "SQ7" },
        { id: "41", label: "TT" },
        { id: "42", label: "TT RS" },
        { id: "43", label: "TTS" }
      ]
    },
    {
      id: "2",
      label: "Bmw",
      shortName: "bmw",
      models: [
        { id: "1", label: "2000" },
        { id: "2", label: "2002" },
        { id: "3", label: "2800" },
        { id: "4", label: "3.0" },
        { id: "5", label: "600" },
        { id: "6", label: "ALPINA" },
        { id: "7", label: "I3" },
        { id: "8", label: "I8" },
        { id: "9", label: "SERIE 1" },
        { id: "10", label: "SERIE 2" },
        { id: "11", label: "SERIE 3" },
        { id: "12", label: "SERIE 3 GT" },
        { id: "13", label: "SERIE 4" },
        { id: "14", label: "SERIE 5" },
        { id: "15", label: "SERIE 5 GT" },
        { id: "16", label: "SERIE 6" },
        { id: "17", label: "SERIE 7" },
        { id: "18", label: "SERIE 8" },
        { id: "19", label: "X1" },
        { id: "20", label: "X2" },
        { id: "21", label: "X3" },
        { id: "22", label: "X4" },
        { id: "23", label: "X5" },
        { id: "24", label: "X6" },
        { id: "25", label: "Z1" },
        { id: "26", label: "Z3" },
        { id: "27", label: "Z4" },
        { id: "28", label: "Z8" }
      ]
    },
    {
      id: "3",
      label: "Citroen",
      shortName: "citroen",
      models: [
        { id: "1", label: "2CV" },
        { id: "2", label: "ACADIANE" },
        { id: "3", label: "AMI" },
        { id: "4", label: "AX" },
        { id: "5", label: "B2" },
        { id: "6", label: "BERLINGO" },
        { id: "7", label: "BX" },
        { id: "8", label: "C-CROSSER" },
        { id: "9", label: "C-ELYSEE" },
        { id: "10", label: "C-ZERO" },
        { id: "11", label: "C1" },
        { id: "12", label: "C15" },
        { id: "13", label: "C2" },
        { id: "14", label: "C25" },
        { id: "15", label: "C3" },
        { id: "16", label: "C3 AIRCROSS" },
        { id: "17", label: "C3 PICASSO" },
        { id: "18", label: "C3 PLURIEL" },
        { id: "19", label: "C35" },
        { id: "20", label: "C4" },
        { id: "21", label: "C4 AIRCROSS" },
        { id: "22", label: "C4 CACTUS" },
        { id: "23", label: "C4 PICASSO" },
        { id: "24", label: "C4 SPACETOURER" },
        { id: "25", label: "C5" },
        { id: "26", label: "C5 AIRCROSS" },
        { id: "27", label: "C6" },
        { id: "28", label: "C8" },
        { id: "29", label: "CX" },
        { id: "30", label: "DS" },
        { id: "31", label: "DS3" },
        { id: "32", label: "DS4" },
        { id: "33", label: "DS5" },
        { id: "34", label: "DYANE" },
        { id: "35", label: "E-MEHARI" },
        { id: "36", label: "EVASION" },
        { id: "37", label: "GRAND C4 PICASSO" },
        { id: "38", label: "GRAND C4 SPACETOURER" },
        { id: "39", label: "GSA" },
        { id: "40", label: "ID" },
        { id: "41", label: "JUMPER" },
        { id: "42", label: "JUMPY" },
        { id: "43", label: "MEHARI" },
        { id: "44", label: "NEMO" },
        { id: "45", label: "PICASSO" },
        { id: "46", label: "SAXO" },
        { id: "47", label: "SM" },
        { id: "48", label: "SPACETOURER" },
        { id: "49", label: "TRACTION" },
        { id: "50", label: "VISA" },
        { id: "51", label: "XANTIA" },
        { id: "52", label: "XM" },
        { id: "53", label: "XSARA" },
        { id: "", label: "ZX" }
      ]
    },
    { id: "4", label: "Ford", shortName: "ford", models: [] },
    { id: "5", label: "Fiat", shortName: "fiat", models: [] },
    { id: "7", label: "Mercedes", shortName: "mercedes", models: [] },
    { id: "8", label: "Opel", shortName: "opel", models: [] },
    { id: "9", label: "Peugeot", shortName: "peugeot", models: [] },
    { id: "10", label: "Renault", shortName: "renault", models: [] },
    { id: "11", label: "Volkswagen", shortName: "volkswagen", models: [] },
    { id: "12", label: "Abarth", shortName: "abarth", models: [] },
    { id: "13", label: "Aleko", models: [] },
    { id: "14", label: "Alfa Romeo", shortName: "alfa-romeo", models: [] },
    { id: "15", label: "Alpina", shortName: "alpina", models: [] },
    { id: "16", label: "Aro", shortName: "aro", models: [] },
    { id: "17", label: "Artega", shortName: "artega", models: [] },
    { id: "18", label: "Aston Martin", shortName: "aston-martin", models: [] },
    { id: "19", label: "Autobianchi", shortName: "autobianchi", models: [] },
    { id: "20", label: "Auverland", shortName: "auverland", models: [] },
    { id: "21", label: "Bentley", shortName: "bentley", models: [] },
    { id: "22", label: "Bertone", shortName: "bertone", models: [] },
    { id: "23", label: "Bluecar Groupe Bollore", models: [] },
    { id: "24", label: "Buick", shortName: "buick", models: [] },
    { id: "25", label: "Cadillac", shortName: "cadillac", models: [] },
    { id: "26", label: "Chevrolet", shortName: "chevrolet", models: [] },
    { id: "27", label: "Chrysler", shortName: "chrysler", models: [] },
    { id: "28", label: "Corvette", shortName: "corvette", models: [] },
    { id: "29", label: "Dacia", shortName: "dacia", models: [] },
    { id: "30", label: "Daewoo", shortName: "daewoo", models: [] },
    { id: "31", label: "Daihatsu", shortName: "daihatsu", models: [] },
    { id: "32", label: "Dangel", shortName: "dangel", models: [] },
    {
      id: "33",
      label: "De La Chapelle",
      shortName: "de-la-chapelle",
      models: []
    },
    { id: "34", label: "Dodge", shortName: "dodge", models: [] },
    { id: "35", label: "Donkervoort", shortName: "donkervoort", models: [] },
    { id: "36", label: "Dr", shortName: "dr-motor", models: [] },
    { id: "37", label: "Ds", shortName: "ds", models: [] },
    { id: "38", label: "Ferrari", shortName: "ferrari", models: [] },
    { id: "39", label: "Fisker", shortName: "fisker", models: [] },
    { id: "40", label: "Gme", models: [] },
    { id: "41", label: "Honda", shortName: "honda", models: [] },
    { id: "42", label: "Hummer", shortName: "hummer", models: [] },
    { id: "43", label: "Hyundai", shortName: "hyundai", models: [] },
    { id: "44", label: "Infiniti", shortName: "infiniti", models: [] },
    { id: "45", label: "Innocenti" },
    { id: "46", label: "Isuzu", shortName: "isuzu", models: [] },
    { id: "47", label: "Iveco", shortName: "iveco", models: [] },
    { id: "48", label: "Jaguar", shortName: "jaguar", models: [] },
    { id: "49", label: "Jeep", shortName: "jeep", models: [] },
    { id: "50", label: "Kia", shortName: "kia", models: [] },
    { id: "51", label: "Lada", shortName: "lada", models: [] },
    { id: "52", label: "Lamborghini", shortName: "lamborghini", models: [] },
    { id: "53", label: "Lancia", shortName: "lancia", models: [] },
    { id: "54", label: "Land Rover", shortName: "land-rover", models: [] },
    { id: "55", label: "Lexus", shortName: "lexus", models: [] },
    { id: "56", label: "Lotus", shortName: "lotus", models: [] },
    { id: "57", label: "Mahindra", shortName: "mahindra", models: [] },
    { id: "58", label: "Maruti", shortName: "maruti", models: [] },
    { id: "59", label: "Maserati", shortName: "maserati", models: [] },
    { id: "60", label: "Mastretta", models: [] },
    { id: "61", label: "Maybach", shortName: "maybach", models: [] },
    { id: "62", label: "Mazda", shortName: "mazda", models: [] },
    { id: "63", label: "Mclaren", shortName: "mclaren", models: [] },
    { id: "64", label: "Mega", shortName: "mega", models: [] },
    { id: "65", label: "Mg", shortName: "mg", models: [] },
    { id: "66", label: "Mia", shortName: "mia-electric", models: [] },
    { id: "67", label: "Mini", shortName: "mini", models: [] },
    { id: "68", label: "Mitsubishi", shortName: "mitsubishi", models: [] },
    { id: "69", label: "Morgan", shortName: "morgan", models: [] },
    { id: "70", label: "Nissan", shortName: "nissan", models: [] },
    { id: "71", label: "Pgo", shortName: "pgo", models: [] },
    { id: "72", label: "Piaggio", shortName: "piaggio", models: [] },
    { id: "73", label: "Polski/fso", shortName: "polski", models: [] },
    { id: "74", label: "Pontiac", shortName: "pontiac", models: [] },
    { id: "75", label: "Porsche", shortName: "porsche", models: [] },
    { id: "76", label: "Proton", shortName: "proton", models: [] },
    { id: "77", label: "Rolls-royce", shortName: "rolls-royce", models: [] },
    { id: "78", label: "Rover", shortName: "rover", models: [] },
    { id: "79", label: "Saab", shortName: "saab", models: [] },
    { id: "80", label: "Santana", shortName: "santana", models: [] },
    { id: "81", label: "Seat", shortName: "seat", models: [] },
    { id: "82", label: "Shuanghuan", shortName: "shuanghuan", models: [] },
    { id: "83", label: "Skoda", shortName: "skoda", models: [] },
    { id: "84", label: "Smart", shortName: "smart", models: [] },
    { id: "85", label: "Ssangyong", shortName: "ssangyong", models: [] },
    { id: "86", label: "Subaru", shortName: "subaru", models: [] },
    { id: "87", label: "Suzuki", shortName: "suzuki", models: [] },
    { id: "88", label: "Talbot", shortName: "talbot-simca", models: [] },
    { id: "89", label: "Tavria", models: [] },
    { id: "90", label: "Tesla", shortName: "tesla", models: [] },
    { id: "91", label: "Toyota", shortName: "toyota", models: [] },
    { id: "92", label: "Tvr", shortName: "tvr", models: [] },
    { id: "93", label: "Venturi", shortName: "venturi", models: [] },
    { id: "94", label: "Volvo", shortName: "volvo", models: [] },
    { id: "95", label: "Autres" }
  ];
  public categories: any[] = [
    { id: "-1", label: "EMPLOYMENT", disabled: true },
    { id: "1", label: "Job offers" },
    { id: "-2", label: "VEHICLES", disabled: true },
    { id: "2", label: "Cars" },
    { id: "3", label: "Motorcycles" },
    { id: "4", label: "Caravanning" },
    { id: "5", label: "Utilities" },
    { id: "6", label: "Auto Equipment" },
    { id: "7", label: "Moto equipment" },
    { id: "8", label: "Caravanning Equipment" },
    { id: "9", label: "Boating" },
    { id: "10", label: "Equipment Nautisme" },
    { id: "-3", label: "IMMOVABLE", disabled: true },
    { id: "11", label: "Sales" },
    { id: "12", label: "Rentals" },
    { id: "13", label: "Roommates" },
    { id: "14", label: "Commercial Offices" },
    { id: "-4", label: "HOLIDAYS", disabled: true },
    { id: "15", label: "Holiday Rentals" },
    { id: "16", label: "Bed and Breakfast" },
    { id: "17", label: "Campsites" },
    { id: "18", label: "Hotels" },
    { id: "19", label: "Unusual accommodations" },
    { id: "-5", label: "MULTIMEDIA", disabled: true },
    { id: "20", label: "Computer science" },
    { id: "21", label: "Consoles & Video Games" },
    { id: "22", label: "Image & Sound" },
    { id: "23", label: "Telephony" },
    { id: "-6", label: "HOUSE", disabled: true },
    { id: "24", label: "Furnishing" },
    { id: "25", label: "Appliances" },
    { id: "26", label: "Tableware" },
    { id: "27", label: "Decoration" },
    { id: "28", label: "Linen" },
    { id: "29", label: "DIY" },
    { id: "30", label: "Gardening" },
    { id: "31", label: "Clothing" },
    { id: "32", label: "Shoes" },
    { id: "33", label: "Accessories & Luggage" },
    { id: "34", label: "Watches & Jewelry" },
    { id: "35", label: "baby equipment" },
    { id: "36", label: "Baby clothes" },
    { id: "-7", label: "HOBBIES", disabled: true },
    { id: "37", label: "DVD / Movies" },
    { id: "38", label: "CD / Music" },
    { id: "39", label: "Books" },
    { id: "40", label: "Animals" },
    { id: "41", label: "Bicycles" },
    { id: "42", label: "Sports" },
    { id: "43", label: "musical instruments" },
    { id: "44", label: "Collection" },
    { id: "45", label: "Toys Games" },
    { id: "46", label: "Gastronomy Wines" },
    { id: "-8", label: "PROFESSIONAL EQUIPMENT", disabled: true },
    { id: "47", label: "Agricultural Equipment" },
    { id: "48", label: "Transport - Handling" },
    { id: "49", label: "Construction - Construction site" },
    { id: "50", label: "Tools - Materials 2nd-work" },
    { id: "51", label: "Industrial Equipment" },
    { id: "52", label: "Catering - Hotels" },
    { id: "53", label: "Office Supplies" },
    { id: "54", label: "Shops & Markets" },
    { id: "55", label: "Medical Equipment" },
    { id: "-9", label: "SERVICES", disabled: true },
    { id: "56", label: "Services" },
    { id: "57", label: "Ticket" },
    { id: "58", label: "Events" },
    { id: "59", label: "Private lessons" },
    { id: "60", label: "Carpool" },
    { id: "-10", label: "OTHERS", disabled: true },
    { id: "61", label: "Other" }
  ];

  public announcement: any = {
    id: "",
    title: "",
    type: 0,
    amount: 0,
    description: "",
    files: [],
    criteria: {},
    location: {
      address: "",
      city: "",
      country: ""
    },
    owner: {
      gender: 0,
      firstName: "",
      lastName: "",
      email: "",
      phone: "",
      address: "",
      hidePhone: true,
      contactMeBack: false
    }
  };
  public announcementTitle: string = "";

  get years() {
    let yearItem = [];
    for (let i = 1; i < 21; i++) {
      let y = { id: i, label: 2020 - i };
      yearItem.push(y);
    }
    return yearItem;
  }
  public handelCategorySelectChange(selected: any) {
    if (selected && selected.id) {
      this.selectedCategory = selected;
      this.announcement.criteria = this.createDefautAnnouncement(selected);
    }
  }
  public handelMarkSelectChange(selected: any) {
    if (selected && selected.id) {
      this.selectedMark = selected;
      this.announcement.criteria.mark = selected.label;
    }
  }

  public handelModelSelectChange(selected: any) {
    if (selected && selected.id) {
      this.selectedModel = selected;
      this.announcement.criteria.model = selected.label;
    }
  }

  public handelYearSelectChange(selected: any) {
    if (selected && selected.id) {
      this.selectedYear = selected;
      this.announcement.criteria.year = selected.label;
    }
  }

  public handelTypeOfFuelSelectChange(selected: any) {
    if (selected && selected.id) {
      this.selectedTypeOfFuel = selected;
      this.announcement.criteria.fuel = selected.label;
    }
  }

  public handelTypeOfGearBoxSelectChange(selected: any) {
    if (selected && selected.id) {
      this.selectedTypeOfGearBox = selected;
      this.announcement.criteria.gearBox = selected.label;
    }
  }

  public createDefautAnnouncement(category: any) {
    let criteria: any = {};
    this.parsedId = parseInt(category.id);

    criteria.category = this.parsedId;
    if (this.parsedId > 1 && this.parsedId < 6) {
      criteria.model = "";
      criteria.fuel = "";
      criteria.mileage = "";
    }
    if (this.parsedId === 2) {
      criteria.mark = "";
      criteria.year = "";
      criteria.gearBox = "";
    }

    if (this.parsedId === 3) {
      criteria.cylinderVolume = "";
    }

    if (this.parsedId > 10 && this.parsedId < 15) {
      criteria.energyClassification = "";
      criteria.sizeOfRoome = "";
      criteria.ges = "";
    }
    if (this.parsedId > 10 && this.parsedId < 13) {
      criteria.typeOfImmo = "";
      criteria.numberOfRooms = 0;
    }
    if (this.parsedId === 12) {
      criteria.isEquiped = false;
    }
    if (this.parsedId === 13) {
      criteria.numberOfRooms = 0;
    }
    if (this.parsedId > 14 && this.parsedId < 19) {
      criteria.hasSwiminpool = false;
      criteria.capacity = 0;
      criteria.numberOfRooms = 0;
    }
    return criteria;
  }
}
</script>
