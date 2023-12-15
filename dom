// import { createGuestList } from './data/guestdata.js';
const createGuestList = require('./data/guestdata.js');
const guestList = createGuestList();
function guestForm() {
  //provide initial guests data list created from GuestManagement class
  let guests = guestList;

  // 1. register event for searching and adding
  function registerEventHandling() {
    const inputSearch = document.getElementById('search-input');
    const addGusetbtn = document.getElementById('add-guest-btn');
    inputSearch.addEventListener('keyup', searchGuest);
    addGusetbtn.addEventListener('click', addGuest);
  }

  // 2. Function to display one guest in the display area
  function displayGuest(guestItem = { firstname, lastname }) {
    const html = `
<div>
  <span>${guestItem.firstname} ${guestItem.lastname}</span>
  <span class="remove-icon" id="${guestItem.firstname}-${guestItem.lastname}" style="cursor:pointer;color:red">[X]</span>
<div>
    `;
    const displayArea = document.getElementById('display-area');
    displayArea.insertAdjacentHTML('beforeend', html);
    const removeBtn = document.getElementById(
      `${guestItem.firstname}-${guestItem.lastname}`
    );
    removeBtn.addEventListener('click', removeGuest);
  }

  // 3. Function to display all existing guests in the display area
  function displayGuests(
    guestResult = [
      { firstname, lastname },
      { firstname, lastname },
    ]
  ) {
    const displayArea = document.getElementById('display-area');
    displayArea.textContent = '';
    guestResult.forEach((guestItem) => displayGuest(guestItem));
  }

  // 4. Function to search and display matching guests
  function searchGuest(event = new Event()) {
    const keyword = event.target.value;
    const result = guests.searchGuests(keyword);
    displayGuests(result);
  }

  // 5. Function to add a new guest
  function addGuest() {
    let firstname = document.getElementById('firstname-input');
    let lastname = document.getElementById('lastname-input');
    guests.addNewGuest(firstname.value, lastname.value);
    displayGuest({ firstname: firstname.value, lastname: lastname.value });
    firstname.value = '';
    lastname.value = '';
  }

  // 6. Function to remove a guest
  function removeGuest(event = new Event()) {
    const parentNode = event.target.parentNode;
    const [firstname, lastname] = event.target.getAttribute('id').split('-');
    parentNode.remove();
    guests.removeGuest({ firstname, lastname });
  }

  return {
    registerEventHandling,
    displayGuests,
    searchGuest,
    addGuest,
    removeGuest,
  };
}
module.exports = guestForm;
// export { guestForm };
// const { registerEventHandling, displayGuests } = guestForm();

// registerEventHandling();
// displayGuests(guestList.getAllGuests());
