# ASSIGNMENT 4 – CO4 Report
**Mohammed Harsath N – 192511097**

## Task 1 – GUI Design Review
Deficiencies identified:
1. All logic inside ActionListener – no separation of UI and service.
2. String comparison with == instead of equals.
3. No validation of empty / non-numeric amount.
4. DB work + Thread.sleep on EDT → UI freezes.
5. Receipt button does nothing.
6. SQL injection risk (string concatenation).
7. Connection never closed; window has no WindowListener.
8. Checked exceptions not handled.

Redesign: FeeWindow only collects input and shows results; FeeService validates and performs payment on a background thread (SwingWorker). Each button gets its own listener or Action.

## Task 2 – Hospital Appointment Desk
Event table, containment tree (Frame → BorderLayout panels → Choice, List, Buttons) and handler pseudocode are documented. Doctor list is kept in a Map<String,List<Doctor>> loaded once.

## Task 3 – Library Search Layout
Outer BorderLayout: NORTH = search FlowLayout panel, CENTER = results (ScrollPane), SOUTH = button FlowLayout panel. Results grow on resize; search and buttons keep preferred size.

## Task 4 – DrawPad forensics
Defect 1: method named mouseclicked (wrong case) → never called.  
Defect 2: drawing with getGraphics() is lost on repaint.  
Repair: store Points, call repaint(), draw in paint(). @Override would have caught the misspelling at compile time.
