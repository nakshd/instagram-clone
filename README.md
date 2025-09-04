<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Madhuri Reddy - Instagram Clone with Username Login</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"
  />
  <link
    href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap"
    rel="stylesheet"
  />
  <style>
    body {
      font-family: "Roboto", sans-serif;
    }
    .scrollbar-hide::-webkit-scrollbar {
      display: none;
    }
    .scrollbar-hide {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }
  </style>
</head>
<body class="bg-white text-gray-900 min-h-screen flex flex-col">

  <!-- Modal Overlay -->
  <div
    id="loginModal"
    class="fixed inset-0 bg-black bg-opacity-60 flex items-center justify-center z-50"
    role="dialog"
    aria-modal="true"
    aria-labelledby="loginTitle"
  >
    <div
      class="bg-white rounded-lg shadow-lg max-w-md w-full p-8 relative"
    >
      <button
        id="closeModalBtn"
        aria-label="Close login modal"
        class="absolute top-4 right-4 text-gray-500 hover:text-gray-900 focus:outline-none"
      >
        <i class="fas fa-times text-xl"></i>
      </button>
      <h2
        id="loginTitle"
        class="text-3xl font-bold text-center mb-6 text-pink-600 select-none"
      >
        Madhuri Reddy
      </h2>
      <form id="loginForm" class="space-y-6" novalidate>
        <div>
          <label
            for="loginIdentifier"
            class="block text-sm font-semibold text-gray-700 mb-1"
            >Username or Email</label
          >
          <input
            type="text"
            id="loginIdentifier"
            name="loginIdentifier"
            required
            placeholder="Username or you@example.com"
            class="w-full border border-gray-300 rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-pink-500"
            autocomplete="username"
            aria-describedby="loginIdentifierError"
          />
          <p
            id="loginIdentifierError"
            class="text-xs text-red-600 mt-1 hidden"
            aria-live="polite"
          >
            Please enter a valid username or email.
          </p>
        </div>
        <div>
          <label
            for="password"
            class="block text-sm font-semibold text-gray-700 mb-1"
            >Password</label
          >
          <input
            type="password"
            id="password"
            name="password"
            required
            placeholder="********"
            class="w-full border border-gray-300 rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-pink-500"
            autocomplete="current-password"
            minlength="6"
            aria-describedby="passwordError"
          />
          <p
            id="passwordError"
            class="text-xs text-red-600 mt-1 hidden"
            aria-live="polite"
          >
            Password must be at least 6 characters.
          </p>
        </div>
        <button
          type="submit"
          class="w-full bg-pink-600 hover:bg-pink-700 text-white font-semibold py-2 rounded-md transition-colors"
        >
          Log In
        </button>
      </form>
      <p class="text-center text-sm text-gray-600 mt-6">
        Don't have an account?
        <button
          id="showRegisterBtn"
          class="text-pink-600 font-semibold hover:underline focus:outline-none"
        >
          Sign up
        </button>
      </p>
    </div>
  </div>

  <!-- Register Modal -->
  <div
    id="registerModal"
    class="fixed inset-0 bg-black bg-opacity-60 flex items-center justify-center z-50 hidden"
    role="dialog"
    aria-modal="true"
    aria-labelledby="registerTitle"
  >
    <div
      class="bg-white rounded-lg shadow-lg max-w-md w-full p-8 relative"
    >
      <button
        id="closeRegisterModalBtn"
        aria-label="Close register modal"
        class="absolute top-4 right-4 text-gray-500 hover:text-gray-900 focus:outline-none"
      >
        <i class="fas fa-times text-xl"></i>
      </button>
      <h2
        id="registerTitle"
        class="text-3xl font-bold text-center mb-6 text-pink-600 select-none"
      >
        Create Account
      </h2>
      <form id="registerForm" class="space-y-6" novalidate>
        <div>
          <label
            for="regName"
            class="block text-sm font-semibold text-gray-700 mb-1"
            >Full Name</label
          >
          <input
            type="text"
            id="regName"
            name="regName"
            required
            placeholder="Your full name"
            class="w-full border border-gray-300 rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-pink-500"
            autocomplete="name"
          />
          <p
            id="regNameError"
            class="text-xs text-red-600 mt-1 hidden"
            aria-live="polite"
          >
            Please enter your full name.
          </p>
        </div>
        <div>
          <label
            for="regUsername"
            class="block text-sm font-semibold text-gray-700 mb-1"
            >Username</label
          >
          <input
            type="text"
            id="regUsername"
            name="regUsername"
            required
            placeholder="Choose a username"
            class="w-full border border-gray-300 rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-pink-500"
            autocomplete="username"
          />
          <p
            id="regUsernameError"
            class="text-xs text-red-600 mt-1 hidden"
            aria-live="polite"
          >
            Please enter a valid username (no spaces).
          </p>
        </div>
        <div>
          <label
            for="regEmail"
            class="block text-sm font-semibold text-gray-700 mb-1"
            >Email</label
          >
          <input
            type="email"
            id="regEmail"
            name="regEmail"
            required
            placeholder="you@example.com"
            class="w-full border border-gray-300 rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-pink-500"
            autocomplete="email"
          />
          <p
            id="regEmailError"
            class="text-xs text-red-600 mt-1 hidden"
            aria-live="polite"
          >
            Please enter a valid email.
          </p>
        </div>
        <div>
          <label
            for="regPassword"
            class="block text-sm font-semibold text-gray-700 mb-1"
            >Password</label
          >
          <input
            type="password"
            id="regPassword"
            name="regPassword"
            required
            placeholder="********"
            class="w-full border border-gray-300 rounded-md px-4 py-2 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:border-pink-500"
            minlength="6"
            autocomplete="new-password"
          />
          <p
            id="regPasswordError"
            class="text-xs text-red-600 mt-1 hidden"
            aria-live="polite"
          >
            Password must be at least 6 characters.
          </p>
        </div>
        <button
          type="submit"
          class="w-full bg-pink-600 hover:bg-pink-700 text-white font-semibold py-2 rounded-md transition-colors"
        >
          Sign Up
        </button>
      </form>
      <p class="text-center text-sm text-gray-600 mt-6">
        Already have an account?
        <button
          id="showLoginBtn"
          class="text-pink-600 font-semibold hover:underline focus:outline-none"
        >
          Log in
        </button>
      </p>
    </div>
  </div>

  <!-- Navbar -->
  <nav
    class="border-b border-gray-300 fixed top-0 left-0 right-0 bg-white z-50"
    aria-label="Primary Navigation"
  >
    <div
      class="max-w-6xl mx-auto px-4 flex items-center justify-between h-16"
    >
      <div class="flex items-center space-x-2">
        <img
          alt="Madhuri Reddyit logo, stylized MR letters in black on white background"
          class="w-8 h-8"
          height="32"
          src="https://storage.googleapis.com/a1aa/image/778306e6-0acb-4c50-fc49-3b70178a5560.jpg"
          width="32"
        />
        <h1
          class="text-2xl font-bold tracking-tight cursor-pointer select-none"
          tabindex="0"
          id="navBrand"
        >
          <span class="text-pink-600">Madhuri</span><span> Reddyit</span>
        </h1>
      </div>
      <div class="hidden md:flex items-center space-x-4">
        <div class="relative text-gray-500 focus-within:text-gray-700">
          <input
            aria-label="Search"
            class="bg-gray-100 rounded-md pl-10 pr-4 py-1 focus:outline-none focus:ring-2 focus:ring-pink-500 focus:bg-white"
            placeholder="Search"
            type="text"
            id="searchInput"
            autocomplete="off"
          />
          <i
            class="fas fa-search absolute left-3 top-1/2 -translate-y-1/2 pointer-events-none"
          ></i>
          <ul
            id="searchResults"
            class="absolute bg-white border border-gray-300 rounded-md mt-1 max-h-48 overflow-y-auto w-full hidden z-50"
            role="listbox"
            aria-label="Search results"
          ></ul>
        </div>
      </div>
      <div class="flex items-center space-x-4" id="navButtonsLoggedOut">
        <button
          id="openLoginBtn"
          class="text-pink-600 font-semibold hover:underline focus:outline-none"
          aria-haspopup="dialog"
          aria-controls="loginModal"
        >
          Log In
        </button>
        <button
          id="openRegisterBtn"
          class="text-white bg-pink-600 hover:bg-pink-700 font-semibold py-1.5 px-4 rounded-md focus:outline-none focus:ring-2 focus:ring-pink-500"
          aria-haspopup="dialog"
          aria-controls="registerModal"
        >
          Sign Up
        </button>
      </div>
      <div
        class="hidden items-center space-x-4"
        id="navButtonsLoggedIn"
        aria-label="User menu"
      >
        <button
          aria-label="Home"
          class="text-2xl text-gray-700 hover:text-pink-600"
          title="Home"
        >
          <i class="fas fa-home"></i>
        </button>
        <button
          aria-label="Messenger"
          class="text-2xl text-gray-700 hover:text-pink-600 relative"
          title="Messenger"
        >
          <i class="far fa-paper-plane"></i>
          <span
            class="absolute -top-1 -right-2 bg-red-500 text-white text-xs rounded-full px-1.5"
            >3</span
          >
        </button>
        <button
          aria-label="New Post"
          class="text-2xl text-gray-700 hover:text-pink-600"
          title="New Post"
        >
          <i class="fas fa-plus-square"></i>
        </button>
        <button
          aria-label="Explore"
          class="text-2xl text-gray-700 hover:text-pink-600"
          title="Explore"
        >
          <i class="far fa-compass"></i>
        </button>
        <button
          aria-label="Notifications"
          class="text-2xl text-gray-700 hover:text-pink-600 relative"
          title="Notifications"
        >
          <i class="far fa-heart"></i>
          <span
            class="absolute -top-1 -right-2 bg-red-500 text-white text-xs rounded-full px-1.5"
            >5</span
          >
        </button>
        <div class="relative group" tabindex="0">
          <button
            aria-label="Profile menu"
            class="w-8 h-8 rounded-full overflow-hidden border-2 border-pink-600 hover:border-pink-700 focus:outline-none focus:ring-2 focus:ring-pink-500"
            id="profileMenuBtn"
            aria-haspopup="true"
            aria-expanded="false"
          >
            <img
              alt="User profile picture"
              class="w-full h-full object-cover"
              height="32"
              src="https://storage.googleapis.com/a1aa/image/9c698b00-49c2-4b54-5a5d-925f54a0649e.jpg"
              width="32"
            />
          </button>
          <ul
            id="profileMenu"
            class="hidden absolute right-0 mt-2 w-48 bg-white border border-gray-300 rounded-md shadow-lg py-1 z-50"
            role="menu"
            aria-label="Profile menu"
          >
            <li>
              <button
                class="block w-full text-left px-4 py-2 text-gray-700 hover:bg-pink-100 focus:bg-pink-100 focus:outline-none"
                role="menuitem"
                id="profileMenuProfile"
              >
                Profile
              </button>
            </li>
            <li>
              <button
                class="block w-full text-left px-4 py-2 text-gray-700 hover:bg-pink-100 focus:bg-pink-100 focus:outline-none"
                role="menuitem"
                id="profileMenuSettings"
              >
                Settings
              </button>
            </li>
            <li>
              <button
                class="block w-full text-left px-4 py-2 text-red-600 hover:bg-red-100 focus:bg-red-100 focus:outline-none font-semibold"
                role="menuitem"
                id="profileMenuLogout"
              >
                Log Out
              </button>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </nav>

  <!-- Main content -->
  <main
    class="max-w-6xl mx-auto px-4 pt-20 md:pt-24 flex flex-col md:flex-row gap-6 flex-1"
    id="mainContent"
    aria-live="polite"
  >
    <!-- Left: Feed -->
    <section class="flex-1 max-w-xl" id="feedSection" tabindex="0" aria-label="Posts feed">
      <!-- Stories -->
      <div
        class="border border-gray-300 rounded-md p-4 mb-6 bg-white shadow-sm"
        aria-label="Stories"
      >
        <div class="flex space-x-4 overflow-x-auto scrollbar-hide" role="list">
          <div
            class="flex flex-col items-center space-y-1 min-w-[72px] cursor-pointer"
            role="listitem"
            tabindex="0"
            aria-label="Story from madhuri"
          >
            <div class="w-16 h-16 rounded-full border-2 border-pink-600 p-1">
              <img
                alt="Story thumbnail showing a young woman smiling with a beach background"
                class="rounded-full object-cover w-full h-full"
                height="64"
                src="https://storage.googleapis.com/a1aa/image/71b66f6d-d5f9-4f08-65db-51f1dda26367.jpg"
                width="64"
              />
            </div>
            <span class="text-xs truncate max-w-[72px] text-center">madhuri</span>
          </div>
          <div
            class="flex flex-col items-center space-y-1 min-w-[72px] cursor-pointer"
            role="listitem"
            tabindex="0"
            aria-label="Story from reddy"
          >
            <div class="w-16 h-16 rounded-full border-2 border-pink-600 p-1">
              <img
                alt="Story thumbnail showing a man with sunglasses and city background"
                class="rounded-full object-cover w-full h-full"
                height="64"
                src="https://storage.googleapis.com/a1aa/image/02c6f459-da45-4200-6b27-718f3ade891e.jpg"
                width="64"
              />
            </div>
            <span class="text-xs truncate max-w-[72px] text-center">reddy</span>
          </div>
          <div
            class="flex flex-col items-center space-y-1 min-w-[72px] cursor-pointer"
            role="listitem"
            tabindex="0"
            aria-label="Story from photog"
          >
            <div class="w-16 h-16 rounded-full border-2 border-pink-600 p-1">
              <img
                alt="Story thumbnail showing a person holding a camera in nature"
                class="rounded-full object-cover w-full h-full"
                height="64"
                src="https://storage.googleapis.com/a1aa/image/5b5f882e-da66-4211-775d-4896e743bf2e.jpg"
                width="64"
              />
            </div>
            <span class="text-xs truncate max-w-[72px] text-center">photog</span>
          </div>
          <div
            class="flex flex-col items-center space-y-1 min-w-[72px] cursor-pointer"
            role="listitem"
            tabindex="0"
            aria-label="Story from flora"
          >
            <div class="w-16 h-16 rounded-full border-2 border-pink-600 p-1">
              <img
                alt="Story thumbnail showing a smiling woman with flowers in hair"
                class="rounded-full object-cover w-full h-full"
                height="64"
                src="https://storage.googleapis.com/a1aa/image/2334192a-4450-4cdd-0563-10da90a1e54d.jpg"
                width="64"
              />
            </div>
            <span class="text-xs truncate max-w-[72px] text-center">flora</span>
          </div>
          <div
            class="flex flex-col items-center space-y-1 min-w-[72px] cursor-pointer"
            role="listitem"
            tabindex="0"
            aria-label="Story from mountain"
          >
            <div class="w-16 h-16 rounded-full border-2 border-pink-600 p-1">
              <img
                alt="Story thumbnail showing a man with a mountain background"
                class="rounded-full object-cover w-full h-full"
                height="64"
                src="https://storage.googleapis.com/a1aa/image/82bd5fd1-1777-4aa0-eb0e-70ff07699306.jpg"
                width="64"
              />
            </div>
            <span class="text-xs truncate max-w-[72px] text-center">mountain</span>
          </div>
          <div
            class="flex flex-col items-center space-y-1 min-w-[72px] cursor-pointer"
            role="listitem"
            tabindex="0"
            aria-label="Story from doglover"
          >
            <div class="w-16 h-16 rounded-full border-2 border-pink-600 p-1">
              <img
                alt="Story thumbnail showing a person with a dog in a park"
                class="rounded-full object-cover w-full h-full"
                height="64"
                src="https://storage.googleapis.com/a1aa/image/318c6f50-ea33-4edb-5340-551184c48d0b.jpg"
                width="64"
              />
            </div>
            <span class="text-xs truncate max-w-[72px] text-center">doglover</span>
          </div>
          <div
            class="flex flex-col items-center space-y-1 min-w-[72px] cursor-pointer"
            role="listitem"
            tabindex="0"
            aria-label="Story from coffee"
          >
            <div class="w-16 h-16 rounded-full border-2 border-pink-600 p-1">
              <img
                alt="Story thumbnail showing a person with a coffee cup in a cafe"
                class="rounded-full object-cover w-full h-full"
                height="64"
                src="https://storage.googleapis.com/a1aa/image/cfd24af4-b70b-454b-074d-573df4ac860e.jpg"
                width="64"
              />
            </div>
            <span class="text-xs truncate max-w-[72px] text-center">coffee</span>
          </div>
          <div
            class="flex flex-col items-center space-y-1 min-w-[72px] cursor-pointer"
            role="listitem"
            tabindex="0"
            aria-label="Story from remote"
          >
            <div class="w-16 h-16 rounded-full border-2 border-pink-600 p-1">
              <img
                alt="Story thumbnail showing a person with a laptop working remotely"
                class="rounded-full object-cover w-full h-full"
                height="64"
                src="https://storage.googleapis.com/a1aa/image/9f5e7ba0-4988-4e73-15e6-9eeb8667b939.jpg"
                width="64"
              />
            </div>
            <span class="text-xs truncate max-w-[72px] text-center">remote</span>
          </div>
        </div>
      </div>

      <!-- Posts Feed -->
      <article
        class="bg-white border border-gray-300 rounded-md mb-6 shadow-sm"
        tabindex="0"
        aria-label="Post by madhuri"
      >
        <header class="flex items-center p-4">
          <img
            alt="Profile picture of madhuri reddy, a young woman with black hair and smiling"
            class="w-10 h-10 rounded-full object-cover border-2 border-pink-600"
            height="40"
            src="https://storage.googleapis.com/a1aa/image/ccb8d6c0-0b9f-4d09-35bc-ae1aeef3926c.jpg"
            width="40"
          />
          <div class="ml-3 flex-1">
            <h2 class="font-semibold text-gray-900" id="postUserName-1">madhuri</h2>
            <p class="text-xs text-gray-500">Hyderabad, India</p>
          </div>
          <button
            aria-label="More options"
            class="text-gray-600 hover:text-gray-900"
            title="More options"
          >
            <i class="fas fa-ellipsis-h"></i>
          </button>
        </header>
        <img
          alt="Instagram style post image showing a scenic sunset over a lake with mountains in the background"
          class="w-full object-cover max-h-[600px]"
          height="600"
          src="https://storage.googleapis.com/a1aa/image/a7ace84e-8262-41ad-0381-b29336b42fe1.jpg"
          width="600"
        />
        <div class="p-4">
          <div class="flex items-center space-x-4 mb-2">
            <button
              aria-label="Like post"
              class="text-2xl text-gray-700 hover:text-pink-600 like-btn"
              data-post-id="1"
              aria-pressed="false"
            >
              <i class="far fa-heart"></i>
            </button>
            <button
              aria-label="Comment on post"
              class="text-2xl text-gray-700 hover:text-pink-600"
            >
              <i class="far fa-comment"></i>
            </button>
            <button
              aria-label="Share post"
              class="text-2xl text-gray-700 hover:text-pink-600"
            >
              <i class="far fa-paper-plane"></i>
            </button>
            <button
              aria-label="Save post"
              class="ml-auto text-2xl text-gray-700 hover:text-pink-600"
            >
              <i class="far fa-bookmark"></i>
            </button>
          </div>
          <p class="font-semibold text-gray-900 mb-1" id="likesCount-1">1,234 likes</p>
          <p class="text-sm">
            <span class="font-semibold cursor-pointer hover:underline" id="postUserNameText-1">madhuri</span>
            Enjoying the beautiful sunset at the lake! #nature #sunset
          </p>
          <p class="text-xs text-gray-500 mt-2">2 hours ago</p>
        </div>
      </article>

      <!-- Additional posts omitted for brevity, same as previous code -->
    </section>

    <!-- Right: Sidebar -->
    <aside
      class="hidden lg:block w-80 sticky top-20 self-start"
      aria-label="Sidebar with user info and suggestions"
    >
      <div
        class="bg-white border border-gray-300 rounded-md p-4 shadow-sm"
        tabindex="0"
      >
        <div class="flex items-center space-x-4 mb-4">
          <img
            alt="User profile picture of madhuri reddy, a young woman with black hair and smiling"
            class="w-14 h-14 rounded-full object-cover border-2 border-pink-600"
            height="56"
            src="https://storage.googleapis.com/a1aa/image/69b9c015-b0b2-44d0-c794-dd9493cf5dda.jpg"
            width="56"
            id="sidebarUserAvatar"
          />
          <div>
            <h3 class="font-semibold text-gray-900" id="sidebarUserName">madhuri</h3>
            <p class="text-sm text-gray-500" id="sidebarFullName">Madhuri Reddy</p>
          </div>
          <button
            class="ml-auto text-sm text-pink-600 font-semibold hover:underline focus:outline-none"
            id="sidebarSwitchBtn"
          >
            Switch
          </button>
        </div>
        <div class="flex justify-between mb-3">
          <h4 class="text-sm font-semibold text-gray-500">Suggestions For You</h4>
          <button
            class="text-xs font-semibold text-gray-900 hover:underline focus:outline-none"
            id="sidebarSeeAllBtn"
          >
            See All
          </button>
        </div>
        <ul class="space-y-3" id="suggestionsList">
          <li class="flex items-center justify-between">
            <div class="flex items-center space-x-3">
              <img
                alt="Suggested user profile picture, a young woman with sunglasses"
                class="w-8 h-8 rounded-full object-cover border border-gray-300"
                height="32"
                src="https://storage.googleapis.com/a1aa/image/bff01cc4-c0f8-412f-cbd3-09518904c9b0.jpg"
                width="32"
              />
              <div>
                <p class="text-sm font-semibold text-gray-900">sunnyday</p>
                <p class="text-xs text-gray-500">New to Madhuri Reddyit</p>
              </div>
            </div>
            <button
              class="text-xs text-pink-600 font-semibold hover:underline focus:outline-none follow-btn"
              data-username="sunnyday"
            >
              Follow
            </button>
          </li>
          <!-- Additional suggestions omitted for brevity -->
        </ul>
        <footer class="mt-6 text-xs text-gray-400 space-y-1" tabindex="0">
          <p>Madhuri Reddyit © 2024</p>
          <p>
            About · Help · Press · API · Jobs · Privacy · Terms · Locations ·
            Language
          </p>
        </footer>
      </div>
    </aside>
  </main>

  <!-- Mobile bottom nav -->
  <nav
    class="fixed bottom-0 left-0 right-0 bg-white border-t border-gray-300 flex justify-around items-center h-14 md:hidden z-50"
    aria-label="Mobile Navigation"
  >
    <button aria-label="Home" class="text-2xl text-gray-700 hover:text-pink-600">
      <i class="fas fa-home"></i>
    </button>
    <button aria-label="Search" class="text-2xl text-gray-700 hover:text-pink-600">
      <i class="fas fa-search"></i>
    </button>
    <button aria-label="New Post" class="text-2xl text-gray-700 hover:text-pink-600">
      <i class="fas fa-plus-square"></i>
    </button>
    <button aria-label="Activity" class="text-2xl text-gray-700 hover:text-pink-600">
      <i class="far fa-heart"></i>
    </button>
    <button
      aria-label="Profile"
      class="w-8 h-8 rounded-full overflow-hidden border-2 border-pink-600 hover:border-pink-700 focus:outline-none focus:ring-2 focus:ring-pink-500"
      id="mobileProfileBtn"
    >
      <img
        alt="User profile picture, placeholder avatar with letter U on pink background"
        class="w-full h-full object-cover"
        height="32"
        src="https://storage.googleapis.com/a1aa/image/9c698b00-49c2-4b54-5a5d-925f54a0649e.jpg"
        width="32"
      />
    </button>
  </nav>

  <script>
    // Simple in-memory "database" for demo purposes
    const usersDB = [
      {
        id: 1,
        name: "Madhuri Reddy",
        username: "madhuri",
        email: "madhuri@example.com",
        password: "password123",
        avatar:
          "https://storage.googleapis.com/a1aa/image/9c698b00-49c2-4b54-5a5d-925f54a0649e.jpg",
      },
    ];

    // Simulate posts likes count (postId => likes)
    const postLikes = {
      1: 1234,
      2: 987,
      3: 1102,
      4: 1450,
      5: 2001,
      6: 1789,
      7: 1234,
      8: 1001,
    };

    // Current logged in user (null if none)
    let currentUser = null;

    // Elements
    const loginModal = document.getElementById("loginModal");
    const registerModal = document.getElementById("registerModal");
    const openLoginBtn = document.getElementById("openLoginBtn");
    const openRegisterBtn = document.getElementById("openRegisterBtn");
    const closeModalBtn = document.getElementById("closeModalBtn");
    const closeRegisterModalBtn = document.getElementById("closeRegisterModalBtn");
    const showRegisterBtn = document.getElementById("showRegisterBtn");
    const showLoginBtn = document.getElementById("showLoginBtn");
    const loginForm = document.getElementById("loginForm");
    const registerForm = document.getElementById("registerForm");
    const navButtonsLoggedOut = document.getElementById("navButtonsLoggedOut");
    const navButtonsLoggedIn = document.getElementById("navButtonsLoggedIn");
    const profileMenuBtn = document.getElementById("profileMenuBtn");
    const profileMenu = document.getElementById("profileMenu");
    const profileMenuLogout = document.getElementById("profileMenuLogout");
    const likesButtons = document.querySelectorAll(".like-btn");
    const suggestionsList = document.getElementById("suggestionsList");
    const likesCountElements = {};
    for (const postId in postLikes) {
      likesCountElements[postId] = document.getElementById(`likesCount-${postId}`);
    }
    const sidebarUserName = document.getElementById("sidebarUserName");
    const sidebarFullName = document.getElementById("sidebarFullName");
    const sidebarUserAvatar = document.getElementById("sidebarUserAvatar");
    const navBrand = document.getElementById("navBrand");
    const mobileProfileBtn = document.getElementById("mobileProfileBtn");
    const loginIdentifierInput = document.getElementById("loginIdentifier");
    const loginIdentifierError = document.getElementById("loginIdentifierError");

    // Show/hide modals
    function openLoginModal() {
      loginModal.classList.remove("hidden");
      loginModal.style.display = "flex";
      registerModal.classList.add("hidden");
      loginIdentifierInput.focus();
    }
    function closeLoginModal() {
      loginModal.classList.add("hidden");
    }
    function openRegisterModal() {
      registerModal.classList.remove("hidden");
      registerModal.style.display = "flex";
      loginModal.classList.add("hidden");
      registerForm.regName.focus();
    }
    function closeRegisterModal() {
      registerModal.classList.add("hidden");
    }

    // Toggle profile menu
    function toggleProfileMenu() {
      const expanded = profileMenuBtn.getAttribute("aria-expanded") === "true";
      if (expanded) {
        profileMenu.classList.add("hidden");
        profileMenuBtn.setAttribute("aria-expanded", "false");
      } else {
        profileMenu.classList.remove("hidden");
        profileMenuBtn.setAttribute("aria-expanded", "true");
      }
    }

    // Close profile menu if clicked outside
    document.addEventListener("click", (e) => {
      if (
        !profileMenu.contains(e.target) &&
        !profileMenuBtn.contains(e.target)
      ) {
        profileMenu.classList.add("hidden");
        profileMenuBtn.setAttribute("aria-expanded", "false");
      }
    });

    // Validate email format
    function isValidEmail(email) {
      return /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email);
    }

    // Validate username format (no spaces, alphanumeric + underscores)
    function isValidUsername(username) {
      return /^[a-zA-Z0-9_]+$/.test(username);
    }

    // Login form submit
    loginForm.addEventListener("submit", (e) => {
      e.preventDefault();
      const identifier = loginIdentifierInput.value.trim();
      const passwordInput = loginForm.password;
      const password = passwordInput.value.trim();

      let valid = true;

      if (!identifier) {
        loginIdentifierError.textContent = "Please enter a username or email.";
        loginIdentifierError.classList.remove("hidden");
        valid = false;
      } else {
        loginIdentifierError.classList.add("hidden");
      }

      if (password.length < 6) {
        document.getElementById("passwordError").classList.remove("hidden");
        valid = false;
      } else {
        document.getElementById("passwordError").classList.add("hidden");
      }

      if (!valid) return;

      // Determine if identifier is email or username
      let user = null;
      if (isValidEmail(identifier)) {
        user = usersDB.find(
          (u) => u.email.toLowerCase() === identifier.toLowerCase() && u.password === password
        );
      } else if (isValidUsername(identifier)) {
        user = usersDB.find(
          (u) => u.username.toLowerCase() === identifier.toLowerCase() && u.password === password
        );
      } else {
        loginIdentifierError.textContent = "Invalid username or email format.";
        loginIdentifierError.classList.remove("hidden");
        return;
      }

      if (!user) {
        alert("Invalid username/email or password.");
        return;
      }

      currentUser = user;
      updateUIForLogin();
      closeLoginModal();
      loginForm.reset();
    });

    // Register form submit
    registerForm.addEventListener("submit", (e) => {
      e.preventDefault();
      const nameInput = registerForm.regName;
      const usernameInput = registerForm.regUsername;
      const emailInput = registerForm.regEmail;
      const passwordInput = registerForm.regPassword;
      const nameError = document.getElementById("regNameError");
      const usernameError = document.getElementById("regUsernameError");
      const emailError = document.getElementById("regEmailError");
      const passwordError = document.getElementById("regPasswordError");

      let valid = true;

      if (nameInput.value.trim().length < 2) {
        nameError.classList.remove("hidden");
        valid = false;
      } else {
        nameError.classList.add("hidden");
      }

      if (!isValidUsername(usernameInput.value.trim())) {
        usernameError.classList.remove("hidden");
        valid = false;
      } else {
        usernameError.classList.add("hidden");
      }

      if (!isValidEmail(emailInput.value.trim())) {
        emailError.classList.remove("hidden");
        valid = false;
      } else {
        emailError.classList.add("hidden");
      }

      if (passwordInput.value.trim().length < 6) {
        passwordError.classList.remove("hidden");
        valid = false;
      } else {
        passwordError.classList.add("hidden");
      }

      if (!valid) return;

      // Check if email or username already exists
      if (
        usersDB.some(
          (u) => u.email.toLowerCase() === emailInput.value.trim().toLowerCase()
        )
      ) {
        alert("Email already registered. Please log in.");
        return;
      }
      if (
        usersDB.some(
          (u) => u.username.toLowerCase() === usernameInput.value.trim().toLowerCase()
        )
      ) {
        alert("Username already taken. Please choose another.");
        return;
      }

      // Add new user
      const newUser = {
        id: usersDB.length + 1,
        name: nameInput.value.trim(),
        username: usernameInput.value.trim().toLowerCase(),
        email: emailInput.value.trim(),
        password: passwordInput.value.trim(),
        avatar:
          "https://placehold.co/64x64?text=U&font=roboto&bg=F472B6&txtclr=fff",
      };
      usersDB.push(newUser);
      currentUser = newUser;
      updateUIForLogin();
      closeRegisterModal();
      registerForm.reset();
    });

    // Update UI after login
    function updateUIForLogin() {
      navButtonsLoggedOut.classList.add("hidden");
      navButtonsLoggedIn.classList.remove("hidden");

      // Update profile picture in navbar and sidebar
      const profileImg = profileMenuBtn.querySelector("img");
      profileImg.src = currentUser.avatar;
      profileImg.alt = `Profile picture of ${currentUser.name}`;

      // Update sidebar user info
      sidebarUserName.textContent = currentUser.username;
      sidebarFullName.textContent = currentUser.name;
      sidebarUserAvatar.src = currentUser.avatar;
      sidebarUserAvatar.alt = `User profile picture of ${currentUser.name}`;

      // Update mobile profile picture
      if (mobileProfileBtn) {
        const mobileImg = mobileProfileBtn.querySelector("img");
        if (mobileImg) {
          mobileImg.src = currentUser.avatar;
          mobileImg.alt = `User profile picture of ${currentUser.name}`;
        }
      }

      // Update nav brand to show username after "Madhuri"
      navBrand.innerHTML = `<span class="text-pink-600">Madhuri</span> <span>${currentUser.username}</span>`;
    }

    // Logout
    profileMenuLogout.addEventListener("click", () => {
      currentUser = null;
      navButtonsLoggedOut.classList.remove("hidden");
      navButtonsLoggedIn.classList.add("hidden");
      profileMenu.classList.add("hidden");
      profileMenuBtn.setAttribute("aria-expanded", "false");
      alert("You have been logged out.");

      // Reset profile images and sidebar info to default
      const profileImg = profileMenuBtn.querySelector("img");
      profileImg.src = "https://storage.googleapis.com/a1aa/image/9c698b00-49c2-4b54-5a5d-925f54a0649e.jpg";
      profileImg.alt = "User profile picture";

      sidebarUserName.textContent = "madhuri";
      sidebarFullName.textContent = "Madhuri Reddy";
      sidebarUserAvatar.src = "https://storage.googleapis.com/a1aa/image/69b9c015-b0b2-44d0-c794-dd9493cf5dda.jpg";
      sidebarUserAvatar.alt = "User profile picture of madhuri reddy";

      if (mobileProfileBtn) {
        const mobileImg = mobileProfileBtn.querySelector("img");
        if (mobileImg) {
          mobileImg.src = "https://storage.googleapis.com/a1aa/image/9c698b00-49c2-4b54-5a5d-925f54a0649e.jpg";
          mobileImg.alt = "User profile picture";
        }
      }

      navBrand.innerHTML = `<span class="text-pink-600">Madhuri</span><span> Reddyit</span>`;
    });

    // Open login modal
    openLoginBtn.addEventListener("click", openLoginModal);
    closeModalBtn.addEventListener("click", closeLoginModal);

    // Open register modal
    openRegisterBtn.addEventListener("click", openRegisterModal);
    closeRegisterModalBtn.addEventListener("click", closeRegisterModal);

    // Switch between login and register modals
    showRegisterBtn.addEventListener("click", openRegisterModal);
    showLoginBtn.addEventListener("click", openLoginModal);

    // Profile menu toggle
    profileMenuBtn.addEventListener("click", toggleProfileMenu);

    // Like button functionality
    likesButtons.forEach((btn) => {
      btn.addEventListener("click", () => {
        if (!currentUser) {
          alert("Please log in to like posts.");
          openLoginModal();
          return;
        }
        const postId = btn.getAttribute("data-post-id");
        if (!postId) return;
        // Toggle like icon fill
        const icon = btn.querySelector("i");
        if (icon.classList.contains("far")) {
          icon.classList.remove("far");
          icon.classList.add("fas", "text-pink-600");
          postLikes[postId]++;
          btn.setAttribute("aria-pressed", "true");
        } else {
          icon.classList.remove("fas", "text-pink-600");
          icon.classList.add("far");
          postLikes[postId]--;
          btn.setAttribute("aria-pressed", "false");
        }
        // Update likes count text
        if (likesCountElements[postId]) {
          likesCountElements[postId].textContent = `${postLikes[postId].toLocaleString()} likes`;
        }
      });
    });

    // Follow button functionality (demo only)
    suggestionsList.querySelectorAll(".follow-btn").forEach((btn) => {
      btn.addEventListener("click", () => {
        if (!currentUser) {
          alert("Please log in to follow users.");
          openLoginModal();
          return;
        }
        btn.textContent = "Following";
        btn.classList.remove("text-pink-600");
        btn.classList.add("text-gray-500", "cursor-default");
        btn.disabled = true;
      });
    });

    // Search input with simple filtering (demo)
    const searchInput = document.getElementById("searchInput");
    const searchResults = document.getElementById("searchResults");
    const allUsers = usersDB.concat([
      { username: "sunnyday" },
      { username: "reddy" },
      { username: "photog" },
      { username: "flora" },
      { username: "mountain" },
      { username: "doglover" },
      { username: "coffee" },
      { username: "remote" },
      { username: "beardman" },
      { username: "curlyq" },
      { username: "smiley" },
      { username: "hatlady" },
    ]);

    searchInput.addEventListener("input", () => {
      const query = searchInput.value.trim().toLowerCase();
      if (!query) {
        searchResults.innerHTML = "";
        searchResults.classList.add("hidden");
        return;
      }
      const filtered = allUsers.filter((u) =>
        u.username.toLowerCase().startsWith(query)
      );
      if (filtered.length === 0) {
        searchResults.innerHTML =
          '<li class="px-4 py-2 text-gray-500">No results found</li>';
        searchResults.classList.remove("hidden");
        return;
      }
      searchResults.innerHTML = filtered
        .map(
          (u) =>
            `<li class="px-4 py-2 hover:bg-pink-100 cursor-pointer" role="option" tabindex="0">${u.username}</li>`
        )
        .join("");
      searchResults.classList.remove("hidden");
    });

    // Close search results on click outside or on selection
    document.addEventListener("click", (e) => {
      if (
        !searchResults.contains(e.target) &&
        e.target !== searchInput
      ) {
        searchResults.classList.add("hidden");
      }
    });

    searchResults.addEventListener("click", (e) => {
      if (e.target.tagName === "LI") {
        searchInput.value = e.target.textContent;
        searchResults.classList.add("hidden");
      }
    });

    // Keyboard navigation for search results
    searchInput.addEventListener("keydown", (e) => {
      const items = Array.from(searchResults.querySelectorAll("li"));
      if (items.length === 0) return;
      let index = items.findIndex((item) =>
        item.classList.contains("bg-pink-200")
      );
      if (e.key === "ArrowDown") {
        e.preventDefault();
        if (index < items.length - 1) {
          if (index >= 0) items[index].classList.remove("bg-pink-200");
          index++;
          items[index].classList.add("bg-pink-200");
          items[index].focus();
        }
      } else if (e.key === "ArrowUp") {
        e.preventDefault();
        if (index > 0) {
          items[index].classList.remove("bg-pink-200");
          index--;
          items[index].classList.add("bg-pink-200");
          items[index].focus();
        }
      } else if (e.key === "Enter") {
        e.preventDefault();
        if (index >= 0) {
          searchInput.value = items[index].textContent;
          searchResults.classList.add("hidden");
        }
      }
    });

    // Accessibility: trap focus inside modals when open
    function trapFocus(element) {
      const focusableElements =
        'a[href], area[href], input:not([disabled]), select:not([disabled]), textarea:not([disabled]), button:not([disabled]), iframe, object, embed, [tabindex="0"], [contenteditable]';
      const firstFocusableElement = element.querySelectorAll(focusableElements)[0];
      const focusableContent = element.querySelectorAll(focusableElements);
      const lastFocusableElement = focusableContent[focusableContent.length - 1];

      element.addEventListener("keydown", function (e) {
        let isTabPressed = e.key === "Tab" || e.keyCode === 9;

        if (!isTabPressed) {
          return;
        }

        if (e.shiftKey) {
          // shift + tab
          if (document.activeElement === firstFocusableElement) {
            lastFocusableElement.focus();
            e.preventDefault();
          }
        } else {
          // tab
          if (document.activeElement === lastFocusableElement) {
            firstFocusableElement.focus();
            e.preventDefault();
          }
        }
      });
    }
    trapFocus(loginModal);
    trapFocus(registerModal);

    // Close modals on Escape key
    document.addEventListener("keydown", (e) => {
      if (e.key === "Escape") {
        if (!loginModal.classList.contains("hidden")) {
          closeLoginModal();
        }
        if (!registerModal.classList.contains("hidden")) {
          closeRegisterModal();
        }
        profileMenu.classList.add("hidden");
        profileMenuBtn.setAttribute("aria-expanded", "false");
      }
    });
  </script>
</body>
</html># instagram-clone
