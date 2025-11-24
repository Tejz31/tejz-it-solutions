// Mobile navigation toggle
const navToggle = document.getElementById("navToggle");
const navbar = document.getElementById("navbar");

if (navToggle) {
  navToggle.addEventListener("click", () => {
    navbar.classList.toggle("nav-open");
  });
}

// Close mobile menu on link click
document.querySelectorAll("#navbar a").forEach((link) => {
  link.addEventListener("click", () => {
    if (navbar.classList.contains("nav-open")) {
      navbar.classList.remove("nav-open");
    }
  });
});

// Footer year
const yearSpan = document.getElementById("year");
if (yearSpan) {
  yearSpan.textContent = new Date().getFullYear();
}

// Simple contact form handler
const contactForm = document.getElementById("contactForm");
const formStatus = document.getElementById("formStatus");

if (contactForm && formStatus) {
  contactForm.addEventListener("submit", (e) => {
    e.preventDefault();

    const name = contactForm.name.value.trim();
    const email = contactForm.email.value.trim();
    const subject = contactForm.subject.value.trim();
    const message = contactForm.message.value.trim();

    if (!name || !email || !subject || !message) {
      formStatus.textContent = "Please fill in all required fields.";
      formStatus.style.color = "#f97316";
      return;
    }

    formStatus.textContent = "Thank you! We will get back to you soon.";
    formStatus.style.color = "#22c55e";

    contactForm.reset();
  });
}

// Smooth scroll for internal links
document.querySelectorAll('a[href^="#"]').forEach((anchor) => {
  anchor.addEventListener("click", function (e) {
    const targetId = this.getAttribute("href").slice(1);
    const targetEl = document.getElementById(targetId);

    if (targetEl) {
      e.preventDefault();
      targetEl.scrollIntoView({
        behavior: "smooth",
        block: "start",
      });
    }
  });
});

// Quote modal logic
const openQuoteBtn = document.getElementById("openQuoteBtn");
const quoteModal = document.getElementById("quoteModal");
const closeQuoteBtn = document.getElementById("closeQuoteBtn");
const quoteForm = document.getElementById("quoteForm");
const quoteStatus = document.getElementById("quoteStatus");

if (openQuoteBtn && quoteModal) {
  openQuoteBtn.addEventListener("click", () => {
    quoteModal.classList.add("show");
  });
}

if (closeQuoteBtn && quoteModal) {
  closeQuoteBtn.addEventListener("click", () => {
    quoteModal.classList.remove("show");
  });
}

// Close modal when clicking outside the modal content
if (quoteModal) {
  quoteModal.addEventListener("click", (e) => {
    if (e.target === quoteModal) {
      quoteModal.classList.remove("show");
    }
  });
}

// Handle quote form submit
if (quoteForm && quoteStatus) {
  quoteForm.addEventListener("submit", (e) => {
    e.preventDefault();

    const qname = quoteForm.qname.value.trim();
    const qemail = quoteForm.qemail.value.trim();
    const qservice = quoteForm.qservice.value.trim();
    const qmessage = quoteForm.qmessage.value.trim();

    if (!qname || !qemail || !qservice || !qmessage) {
      quoteStatus.textContent = "Please fill in all required fields.";
      quoteStatus.style.color = "#f97316";
      return;
    }

    quoteStatus.textContent = "Thank you! We will contact you with a quote.";
    quoteStatus.style.color = "#22c55e";

    quoteForm.reset();

    setTimeout(() => {
      quoteModal.classList.remove("show");
      quoteStatus.textContent = "";
    }, 1500);
  });
}
