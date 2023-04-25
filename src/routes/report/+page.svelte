<script>
    let isSending = false;
    let isSuccess = undefined;
    const apiUrl = "https://api.emailjs.com/api/v1.0/email/send";
    const serviceId = "service_3m51yht";
    const templateId = "template_yenxvis";
    const userId = "AjrcS7rexy9RwbHne";
    async function sendMail(mail) {
        const body = JSON.stringify({
            service_id: serviceId,
            template_id: templateId,
            user_id: userId,
            template_params: mail,
        });

        try {
            const res = await fetch(apiUrl, {
                method: "POST",
                body,
                headers: { "Content-Type": "application/json" },
            });
            return res.status === 200;
        } catch {
            return false;
        }
    }

    const handleSubmit = async (e) => {
        e.preventDefault();
        isSending = true;

        const formData = new FormData(e.target);
        const mail = Object.fromEntries(formData);
        const data = {
            user: mail.user,
            to_name: "HappyTails",
            message: [
                `Address: ${mail.address}`,
                `Country: ${mail.country}`,
                `State: ${mail.state}`,
                `City: ${mail.city}`,
                `Animal: ${mail["animal-preference"]}`,
                `Danger: ${mail.danger}`,
                `Others: ${mail["other-questions"]}`,
            ].join("\n"),
        };
        const success = await sendMail(data);
        isSending = false;
        isSuccess = success;
        return isSuccess;
    };
</script>

<div class="my-20">
    <form
        on:submit={handleSubmit}
        class="max-w-md mx-auto mt-8 space-y-6 mt-auto my-10"
        action="http://127.0.0.1:5000/submit"
        method="post"
    >
        <div>
            <div>
                <label
                    class="block font-medium text-gray-700 text-left"
                    for="user">Your Name</label
                >
                <input
                    name="user"
                    class="text-black form-input mt-1 block w-full rounded-md border-gray-300 shadow-sm"
                    id="user"
                    type="text"
                />
            </div>

            <div>
                <label class="block font-medium text-gray-700 text-left" for="email">E-mail</label>
                <input name="email" class="text-black form-input mt-1 block w-full rounded-md border-gray-300 shadow-sm" id="email" type="email">
              </div>

              <div>
                <label class="block font-medium text-gray-700 text-left" for="phone-number">Phone Number</label>
                <input name="phone-number" class="text-black form-input mt-1 block w-full rounded-md border-gray-300 shadow-sm" id="phone-number" type="tel">
              </div>
            <div>
                <label
                    class="block font-medium text-gray-700 text-left"
                    for="address">Location of the animal</label
                >
                <input
                    name="address"
                    class="text-black form-input mt-1 block w-full rounded-md border-gray-300 shadow-sm"
                    id="address"
                    type="text"
                />
            </div>
            <div class="grid grid-cols-3 gap-4">
                <div>
                    <label
                        class="block font-medium text-gray-700 text-left"
                        for="city">City</label
                    >
                    <input
                        name="city"
                        class="text-black form-input mt-1 block w-full rounded-md border-gray-300 shadow-sm"
                        id="city"
                        type="text"
                    />
                </div>
                <div>
                    <label
                        class="block font-medium text-gray-700 text-left"
                        for="state">State</label
                    >
                    <input
                        name="state"
                        class="text-black form-input mt-1 block w-full rounded-md border-gray-300 shadow-sm"
                        id="state"
                        type="text"
                    />
                </div>
                <div>
                    <label
                        class="block font-medium text-gray-700 text-left"
                        for="country">Country</label
                    >
                    <input
                        name="country"
                        class="text-black form-input mt-1 block w-full rounded-md border-gray-300 shadow-sm"
                        id="country"
                        type="text"
                    />
                </div>
            </div>

            <label
                class="block font-medium text-gray-700"
                for="animal-preference">What animal did you find?</label
            >
            <select
                name="animal-preference"
                class="text-black form-select mt-1 block w-full rounded-md border-gray-300 shadow-sm"
                id="animal-preference"
            >
                <option value="">Choose here</option>
                <option value="dog">Dog</option>
                <option value="cat">Cat</option>
                <option value="bird">Bird</option>
                <option value="other">Other</option>
            </select>

            <div class="mt-4">
                <label class="block font-medium text-gray-700" for="gender"
                    >Mode of danger</label
                >
                <select
                    name="danger"
                    class="text-black form-select mt-1 block w-full rounded-md border-gray-300 shadow-sm"
                    id="danger"
                >
                    <option value="">Choose here</option>
                    <option value="abandoned">Abandoned</option>
                    <option value="sick">Sick</option>
                    <option value="abuse">Abuse</option>
                </select>
            </div>

            <div class="mt-4">
                <label
                    class="block font-medium text-gray-700"
                    for="other-questions">Give us more details</label
                >
                <textarea
                    class="text-black form-textarea mt-1 block w-full rounded-md border-gray-300 shadow-sm"
                    id="other-questions"
                    name="other-questions"
                    rows="3"
                />
            </div>
            <div class="mt-6">
                <button
                    class="px-4 py-2 bg-indigo-600 border border-transparent rounded-md font-semibold text-white hover:bg-indigo-700 focus:outline-none focus:shadow-outline-indigo focus:border-indigo-700 active:bg-indigo-800 transition duration-150 ease-in-out"
                    >Submit</button
                >
            </div>
        </div>
    </form>
</div>
<!-- <div>
        <label class="block font-medium text-gray-700" for="animal-preference">Animal Preference</label>
        <div class="grid grid-cols-3 gap-4">
          <div>
            <label class="block font-medium text-gray-700" for="color">Color</label>
            <input class="form-input mt-1 block w-full rounded-md border-gray-300 shadow-sm" id="color" type="text">
          </div>
          <div>
            <label class="block font-medium text-gray-700" for="gender">Gender</label>
            <select class="form-select mt-1 block w-full rounded-md border-gray-300 shadow-sm" id="gender">
              <option>Male</option>
              <option>Female</option>
              <option>Other</option>
            </select>
          </div> -->
