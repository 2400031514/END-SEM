const initial = [{ id: 1, name: "Ram", present: false }];

function reducer(s, a) {
  return a.type === "TOGGLE"
    ? s.map(x => x.id === a.id ? { ...x, present: !x.present } : x)
    : s;
}

export default function App() {
  const [st, dispatch] = React.useReducer(reducer, initial);

  return st.map(x => (
    <div key={x.id}>
      {x.name} - {x.present ? "Present" : "Absent"}
      <button onClick={() => dispatch({ type: "TOGGLE", id: x.id })}>
        Toggle
      </button>
    </div>
  ));
}
