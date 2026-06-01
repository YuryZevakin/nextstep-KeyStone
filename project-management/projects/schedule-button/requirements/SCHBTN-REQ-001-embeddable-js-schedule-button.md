# SCHBTN-REQ-001: Embeddable JavaScript Schedule Button for Any HTML Page

## Metadata

- ID: `SCHBTN-REQ-001`
- Status: `Draft`
- Priority: `High`
- Owner: `Product Manager`
- Stakeholders: `Website Visitors, Sales Team, Support Team`
- Created: `2026-06-01`
- Project Key: `SCHBTN`
- Origin Backlog Item: `SCHBTN-IDEA-001`
- Target Release: `TBD`

## Problem Statement

Teams need a scheduling entry point that can be added quickly to any website page without full app integration.

## Business Value

An embeddable schedule button reduces friction for meeting booking and increases conversion from visitor to booked meeting.

## Users / Actors

- Website Visitor
- Website Owner
- Google Calendar / Scheduling Provider

## Requirement

The system must provide a JavaScript code snippet that can be inserted into any HTML page to render a "Schedule" button, and that button must open an in-page dialog that shows a list of available meeting time slots sourced from a connected calendar availability feed.

## Backend Requirement

The backend must provide available-time data for the button dialog through an API endpoint. The endpoint must return a list of available slots with start and end times in a consistent machine-readable format (for example JSON with ISO 8601 timestamps).
The backend must also support setting a selected slot as busy after user booking confirmation, so the slot is no longer returned as available.

## JavaScript Snippet (MVP)

```html
<div id="schedule-button-container"></div>
<script>
  (function () {
    var availabilityApiUrl = "https://example.com/api/availability";
    var label = "Schedule";

    var container = document.getElementById("schedule-button-container");
    if (!container) return;

    var button = document.createElement("button");
    button.type = "button";
    button.textContent = label;
    button.setAttribute("aria-label", "Open scheduling page");
    button.style.padding = "10px 16px";
    button.style.border = "0";
    button.style.borderRadius = "6px";
    button.style.background = "#1a73e8";
    button.style.color = "#ffffff";
    button.style.font = "600 14px Arial, sans-serif";
    button.style.cursor = "pointer";

    var dialog = document.createElement("dialog");
    dialog.setAttribute("aria-label", "Available time slots");
    dialog.style.padding = "16px";
    dialog.style.border = "1px solid #d0d7de";
    dialog.style.borderRadius = "8px";
    dialog.style.maxWidth = "420px";
    dialog.style.width = "90%";

    var title = document.createElement("h3");
    title.textContent = "Available time slots";
    title.style.margin = "0 0 12px";
    title.style.font = "600 18px Arial, sans-serif";

    var status = document.createElement("p");
    status.style.margin = "0 0 12px";
    status.style.font = "400 14px Arial, sans-serif";

    var list = document.createElement("ul");
    list.style.margin = "0";
    list.style.paddingLeft = "20px";
    list.style.font = "400 14px Arial, sans-serif";

    var closeBtn = document.createElement("button");
    closeBtn.type = "button";
    closeBtn.textContent = "Close";
    closeBtn.style.marginTop = "12px";
    closeBtn.addEventListener("click", function () {
      dialog.close();
    });

    dialog.appendChild(title);
    dialog.appendChild(status);
    dialog.appendChild(list);
    dialog.appendChild(closeBtn);
    document.body.appendChild(dialog);

    function renderSlots(slots) {
      list.innerHTML = "";
      if (!Array.isArray(slots) || slots.length === 0) {
        status.textContent = "No available slots.";
        return;
      }
      status.textContent = "";
      slots.forEach(function (slot) {
        var item = document.createElement("li");
        var slotBtn = document.createElement("button");
        slotBtn.type = "button";
        slotBtn.textContent = slot.start + " - " + slot.end;
        slotBtn.style.marginBottom = "8px";
        slotBtn.addEventListener("click", async function () {
          var confirmed = window.confirm("Book this time slot?");
          if (!confirmed) return;
          status.textContent = "Booking slot...";
          try {
            var bookingResponse = await fetch(
              availabilityApiUrl.replace("/availability", "/bookings"),
              {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({ start: slot.start, end: slot.end })
              }
            );
            if (!bookingResponse.ok) throw new Error("Booking failed");
            status.textContent = "Slot booked.";
            item.remove();
          } catch (err) {
            status.textContent = "Unable to book slot. Please try again.";
          }
        });
        item.appendChild(slotBtn);
        list.appendChild(item);
      });
    }

    button.addEventListener("click", async function () {
      status.textContent = "Loading available slots...";
      list.innerHTML = "";
      dialog.showModal();
      try {
        var response = await fetch(availabilityApiUrl, { method: "GET" });
        if (!response.ok) throw new Error("Availability request failed");
        var data = await response.json();
        renderSlots(data.slots);
      } catch (err) {
        status.textContent = "Unable to load slots. Please try again.";
      }
    });

    container.appendChild(button);
  })();
</script>
```

## Acceptance Criteria

- [ ] Snippet can be pasted into a plain HTML file and renders a visible button without build tools.
- [ ] Clicking the button opens an in-page dialog modal.
- [ ] Dialog displays a list of available meeting slots returned from the configured availability API.
- [ ] Backend API returns only currently available (not already booked) slots.
- [ ] Backend API response includes start and end time for each slot.
- [ ] When a user confirms a slot, backend marks that slot as busy/reserved.
- [ ] A slot marked as busy is excluded from subsequent availability responses.
- [ ] Works in latest Chrome, Safari, Firefox, and Edge.
- [ ] Button remains keyboard accessible (`Tab` + `Enter` / `Space`).
- [ ] Dialog remains keyboard accessible (`Tab` navigation + `Esc` to close, or Close button).
- [ ] If container element is missing, script fails safely without breaking the page.

## Non-Functional Requirements

- Performance: `Button render must complete within 100ms after script execution on a normal network/device.`
- Reliability: `Dialog open and slot loading flow should succeed for 99.9% of interactions when API is valid.`
- Security: `Availability API must be authenticated/authorized and must not expose private calendar event details beyond start/end slots.`

## Out of Scope

- Custom backend availability aggregation across multiple calendars.
- Payment processing.
- Automated reminder delivery (email/SMS).

## Dependencies

- Google Calendar integration service that exposes available slots via API endpoint.
- Publicly accessible availability API URL.

## Open Questions

- Should branding, locale, and theme be configurable through data attributes?
- Should slot booking require additional user fields (name/email) before confirmation?
