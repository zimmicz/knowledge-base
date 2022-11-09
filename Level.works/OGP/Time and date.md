## Shift creation

### Frontend

``` javascript
startDate: `${shiftFormData.startDate}T${shiftFormData.startTime}`,
endDate: `${shiftFormData.endDate}T${shiftFormData.endTime}`,
```

### Backend (ogp/shifts.ts)
```
shiftData = { ...shiftData, utcStartDate: startDate, utcEndDate: endDate, timeZone };
const timeZone = 'Europe/Amsterdam'; // hard coded
```

