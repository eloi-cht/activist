<template>
  <div
    class="text-light-text dark:text-dark-text bg-light-content dark:bg-dark-content"
  >
    <Head>
      <Title>{{ title }}</Title>
    </Head>
    <div
      class="flex flex-col items-center w-full responsive-py-4 responsive-px-5"
    >
      <PopupImage v-on:click="togglePopup" />
      <!-- Note: image on top of content. -->
      <img
        v-if="$colorMode.value == 'light'"
        src="/images/content_pages/mockups/grow_organization_light.png"
        alt="Mockups that show mobile event join flow interests selection and web organization affiliates page."
        class="w-full md:hidden h-1/6"
      />
      <img
        v-else-if="$colorMode.value == 'dark'"
        src="/images/content_pages/mockups/grow_organization_dark.png"
        alt="Mockups that show mobile event join flow interests selection and web organization affiliates page."
        class="w-full md:hidden h-1/6"
      />
      <div class="w-10/12 grid grid-cols-1 md:w-full 2xl:grid-cols-2">
        <div class="items-center text-left space-y-4 md:items-start">
          <!-- Note: image floating right of content. -->
          <button 
            v-on:click="togglePopup"
            v-on:keydown.enter="togglePopup"
            id="popup-open-btn"
            class="hidden float-right object-contain p-4 cursor-pointer aspect-square md:block 2xl:hidden h-1/5"
          >
            <img
              v-if="$colorMode.value == 'light'"
              src="/images/content_pages/mockups/grow_organization_light.png"
              alt="Mockups that show mobile event join flow interests selection and web organization affiliates page."
              id="popup-img"
            />
            <img
              v-if="$colorMode.value == 'dark'"
              src="/images/content_pages/mockups/grow_organization_dark.png"
              alt="Mockups that show mobile event join flow interests selection and web organization affiliates page."
              id="popup-img"
            />
          </button>
          <h1 class="pb-2 font-bold responsive-h1">Expand your movement</h1>
          <div class="flex flex-row py-2 space-x-3">
            <Icon
              name="bi:info-circle-fill"
              size="1.25em"
              class="text-light-link-text dark:text-dark-link-text mt-[0.125rem]"
            />
            <p>
              See the
              <a
                href="https://www.figma.com/file/I9McFfaLu1RiiWp5IP3YjE/activist_public_designs?node-id=517%3A4852&t=ytDrcE8K3RrfCxM6-1"
                class="items-center focus-brand link-text"
                target="_blank"
              >
                organization designs on Figma
                <Icon
                  name="bi:box-arrow-up-right"
                  size="1em"
                  style="vertical-align: baseline"
                />
              </a>
              to learn more
            </p>
          </div>
          <p>
            activist is first and foremost about
            <strong>organizations</strong>, with the design of the platform
            being tailored to their needs. The main function of organizations on
            activist is organizing and hosting <strong>events</strong>, but
            future features aim to help them achieve their goals and scale more
            effectively.
          </p>
          <p>
            With activist you can keep track of all your pads, protocols,
            decisions and events in one place while at the same time quickly
            onboarding new joiners to your political actions. We want to inspire
            as well as improve collaboration between organizations because we
            know that we're only going to be able to sustain action together.
          </p>
          <p>
            Of paramount importance to activist's health is the
            <strong>application to join</strong> for all organizations. We'll
            start with a select few that will then help us choose all future
            organizations that join the platform. In this way we hope to instill
            trust in the community — that no organization has not been vouched
            for, and that when interacting with a person they are verified and
            brought in by people that others work with.
          </p>
          <p>
            Long term features will integrate every aspect of an organization's
            political life: making working groups and assigning tasks; releasing
            statements to their supporters; finding and tailoring actions based
            on real life legislation; and much more!
          </p>
          <p class="pb-2 md:pb-4">
            Please use the <strong>Request access</strong> link below to tell us
            more about your organization! We'd also love to hear from you in our
            <a
              href="https://matrix.to/#/#activist_community:matrix.org"
              class="items-center focus-brand link-text"
              target="_blank"
            >
              public Matrix chat rooms
              <Icon
                name="bi:box-arrow-up-right"
                size="1em"
                style="vertical-align: baseline"
              />
            </a>
            so we know how best to help your organization.
          </p>
          <div
            class="flex flex-col items-center space-y-2 md:items-left sm:space-x-4 sm:space-y-0 sm:flex-row"
          >
            <BtnLabeled
              :cta="true"
              label="Request access"
              linkTo="https://tally.so/r/nprxbq"
              fontSize="lg"
              class="w-52"
            />
            <BtnLabeled
              :cta="false"
              label="Return home"
              linkTo="/"
              fontSize="lg"
              class="w-52"
            />
          </div>
        </div>
        <div class="flex justify-end pr-32">
          <!-- Note: image right of content. -->
          <img
            v-if="$colorMode.value == 'light'"
            src="/images/content_pages/mockups/grow_organization_light.png"
            alt="Mockups that show mobile event join flow interests selection and web organization affiliates page."
            class="hidden object-contain cursor-pointer 2xl:block h-3/4"
            v-on:click="togglePopup"
          />
          <img
            v-else-if="$colorMode.value == 'dark'"
            src="/images/content_pages/mockups/grow_organization_dark.png"
            alt="Mockups that show mobile event join flow interests selection and web organization affiliates page."
            class="hidden object-contain cursor-pointer 2xl:block h-3/4"
            v-on:click="togglePopup"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const title = ref("Grow Organization");
</script>

<script popup_image>
import PopupImage from "../../components/Popup/PopupImage";

export default {
  name: "PopupImage",
  components: {
    PopupImage,
  },
};

function togglePopup(event) {
  // Prevent button default behavior
  event.preventDefault();

  // Style image container
  let popup_container = document.getElementById("popup");

  // Handle image
  let image = document.getElementById("popup-image");
  let pop_img = document.getElementById("popup-img");
  image.src = `${pop_img.src}`;

  // Toggle visibility
  popup_container.classList.toggle("hidden");

  // Focus on modal close button
  let pop_close_btn = document.getElementById("popup-close-btn");
  pop_close_btn.focus();
}
</script>
