# Ticket-Booking-System
<!DOCTYPE html>
<html lang="en">

<head>
	<meta charset="UTF-8">
	<meta name="viewport"
		content="width=device-width, initial-scale=1.0">
	<title>Ticket Booking</title>
	<script src="https://cdn.tailwindcss.com"></script>
</head>

<body class="bg-blue-100">
	<div class="min-h-screen flex justify-center items-center">
		<div class="bg-white p-8 rounded-lg shadow-md
					container max-w-md">
			<h2 class="text-2xl font-semibold 
					mb-4 text-center">
				Book Your Tickets
			</h2>
			<form action="#" method="POST" class="space-y-4"
				id="bookingForm" onsubmit="submitForm(event)">
				<div>
					<label for="category"
						class="block text-sm font-medium 
								form-label text-gray-700">
						Category
					</label>
					<select id="category" name="category"
							class="w-full border rounded-md p-2 
								form-select focus:outline-none 
								focus:ring-2 focus:ring-blue-500 
								focus:border-transparent"
							required onchange="changeSeatType()">
						<option value="" disabled selected>
							Select Category
						</option>
						<option value="bus">Bus</option>
						<option value="train">Train</option>
						<option value="movie">Movie</option>
					</select>
				</div>
				<div>
					<label for="timing" class="block text-sm 
											font-medium form-label
											text-gray-700">
						Timing
					</label>
					<select id="timing" name="timing"
							class="w-full border rounded-md p-2 
								form-select focus:outline-none
								focus:ring-2 focus:ring-blue-500 
								focus:border-transparent"
						required>
						<option value="" disabled selected>
						Select Timing
						</option>
						<option value="10am">10:00 AM</option>
						<option value="12pm">12:00 PM</option>
						<option value="1pm">01:00 PM</option>
						<option value="3pm">03:00 PM</option>
						<option value="6pm">06:00 PM</option>
						<option value="8pm">08:00 PM</option>
					</select>
				</div>
				<div>
					<label for="availableSeat"
						class="block text-sm font-medium 
								form-label text-gray-700">
						Available Seat</label>
					<select id="availableSeat" name="availableSeat"
							class="w-full border rounded-md p-2 
								form-select focus:outline-none 
								focus:ring-2 focus:ring-blue-500 
								focus:border-transparent"
						required>
						<option value="" disabled selected>
							Select Available Seat
						</option>
					</select>
				</div>
				<div>
					<label for="name"
						class="block text-sm font-medium
								form-label text-gray-700">
						Name
					</label>
					<input type="text" id="name" name="name"
						class="w-full border rounded-md 
								p-2 form-input focus:outline-none
								focus:ring-2 focus:ring-blue-500
								focus:border-transparent"
							placeholder="Enter name" required>
				</div>
				<div>
					<label for="bookingDate"
						class="block text-sm font-medium
								form-label text-gray-700">
						Booking Date
					</label>
					<input type="date" id="bookingDate"
						name="bookingDate"
							class="w-full border rounded-md p-2
								form-input focus:outline-none
								focus:ring-2 focus:ring-blue-500
								focus:border-transparent"
							required>
				</div>
				<div>
					<label for="seatType"
						class="block text-sm font-medium 
								form-label text-gray-700">
						Seat Type
					</label>
					<select id="seatType" name="seatType"
							class="w-full border rounded-md p-2 
								form-select focus:outline-none 
								focus:ring-2 focus:ring-blue-500
								focus:border-transparent"
						required>
						<option value="" disabled selected>
							Select Seat Type
						</option>
					</select>
				</div>
				<div>
					<button type="submit"
							class="w-full bg-blue-500 text-white 
								py-2 rounded-md hover:bg-blue-600
								transition-colors form-button">
						Book Now
					</button>
				</div>
			</form>
			<div id="bookingDetails"
				class="hidden mt-4 booking-details
						text-gray-700">
				<h3 class="text-xl font-semibold">
					Booking Details:
				</h3>
				<p id="categoryDisplay"></p>
				<p id="timingDisplay"></p>
				<p id="availableSeatDisplay"></p>
				<p id="nameDisplay"></p>
				<p id="bookingDateDisplay"></p>
				<p id="seatTypeDisplay"></p>
				<p class="text-green-500 font-semibold 
						success-message" 
				id="successMessage">
				</p>
				<button id="downloadTicketBtn"
						class="bg-blue-500 text-white px-4 
							py-2 rounded-md mt-2 hidden">
					Download Ticket
				</button>
			</div>
		</div>
	</div>
	<script>
		function submitForm(event) {
			event.preventDefault();
			const category = document.getElementById('category').value;
			const timing = document.getElementById('timing').value;
			const availableSeat = document.getElementById('availableSeat')
										.value;
			const name = document.getElementById('name').value;
			const bookingDate = document.getElementById('bookingDate')
										.value;
			const seatType = document.getElementById('seatType').value;
			document.getElementById('categoryDisplay')
					.textContent = `Category: ${category}`;
			document.getElementById('timingDisplay')
					.textContent = `Timing: ${timing}`;
			document.getElementById('availableSeatDisplay')
					.textContent = `Available Seat: ${availableSeat}`;
			document.getElementById('nameDisplay')
					.textContent = `Name: ${name}`;
			document.getElementById('bookingDateDisplay')
					.textContent = `Booking Date: ${bookingDate}`;
			document.getElementById('seatTypeDisplay')
					.textContent = `Seat Type: ${seatType}`;
			document.getElementById('successMessage')
					.textContent = 'Booking Successful!';
			document.getElementById('bookingDetails')
					.classList.remove('hidden');
			document.getElementById('downloadTicketBtn')
					.classList.remove('hidden');
			document.getElementById('downloadTicketBtn')
					.onclick = downloadTicket;
		}
		function downloadTicket() {
			const category = document.getElementById('category').value;
			const timing = document.getElementById('timing')
								.value;
			const availableSeat = document.getElementById('availableSeat')
										.value;
			const name = document.getElementById('name').value;
			const bookingDate = document.getElementById('bookingDate')
										.value;
			const seatType = document.getElementById('seatType')
									.value;
			const ticketContent = `Category: ${category}\nTiming: 
								${timing}\nAvailable Seat: 
								${availableSeat}\nName: 
								${name}\nBooking Date: 
								${bookingDate}\nSeat Type: 
								${seatType}`;
			const blob = new Blob([ticketContent], { type: 'text/plain' });
			const link = document.createElement('a');
			link.href = window.URL.createObjectURL(blob);
			link.download = 'ticket.txt';
			link.click();
		}
		function changeSeatType() {
			const category = document.getElementById('category').value;
			const seatTypeSelect = document.getElementById('seatType');
			seatTypeSelect.innerHTML = '';

			// Select the availableSeat dropdown element
			const availableSeatSelect =document.getElementById('availableSeat');

			// Clear the options
			availableSeatSelect.innerHTML = '';
			if (category === 'bus' || category === 'train') {
				const seatOptions = ['General', 'Sleeper', 'AC'];
				seatOptions.forEach(option => {
					const optionElement = document.createElement('option');
					optionElement.value = option.toLowerCase();
					optionElement.textContent = option;
					seatTypeSelect.appendChild(optionElement);
				});
			} else if (category === 'movie') {
				const seatOptions = ['Standard', 'Premium', 'VIP'];
				seatOptions.forEach(option => {
					const optionElement = document.createElement('option');
					optionElement.value = option.toLowerCase();
					optionElement.textContent = option;
					seatTypeSelect.appendChild(optionElement);
				});
			}
			for (let i = 1; i <= 30; i++) {
				const optionElement = document.createElement('option');
				optionElement.value = i;
				optionElement.textContent = i;
				availableSeatSelect.appendChild(optionElement);
			}
		}
		window.onload = changeSeatType;
	</script>
</body>

</html>
