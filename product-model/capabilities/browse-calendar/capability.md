---
availability:
- place: desktop
- place: command-line
references:
- kind: code
  role: implementation
  target: Features/Calendar/CalendarController.cs
- kind: code
  role: implementation
  target: Services/EventStore.Queries.cs
- kind: code
  role: implementation
  target: Services/Recurrence.cs
- kind: code
  role: implementation
  target: Views/AgendaView.cs
- kind: code
  role: implementation
  target: Views/TimeGridViews.cs
- kind: code
  role: implementation
  target: Views/MonthView.xaml.cs
- kind: code
  role: implementation
  target: Shell/DayAgendaPanel.cs
- kind: code
  role: implementation
  target: Killendar.Cli/Program.cs
---

# Browse calendar

Read appointments by calendar period or selected day, with the dates of repeating series shown where they fall. The desktop offers Month, Week, Day and Agenda; the command line returns a bounded agenda of up to 31 days.
