# Deleting Notes

As you keep notes during your investigation, you will eventually find that some of the notes are no longer relevant, and you want to remove them from your personal notes API. In this chapter, you are going to be refactoring your notes list to add a delete button which, when clicked, will delete the corresponding note from the API.

## Adding Delete Button

In your note HTML representation, add the following button.

> #### `glassdale/scripts/notes/Note.js`

```js
<button id="deleteNote--${noteObject.id}">Delete</button>
```


## Adding a DELETE Operation

Add a new method to your note data provider with a fetch that uses the DELETE method.

> #### `glassdale/scripts/notes/NoteProvider.js`

```js
const deleteNote = noteId => {
    return fetch(`http://localhost:8088/notes/${noteId}`, {
        method: "DELETE"
    })
}
```

## Handling Delete Button Click

In your notecomponent, add a new event listener to the event hub that captures any delete button click. Check the 

> #### `glassdale/scripts/notes/Note.js`

```js
const eventHub = document.querySelector(".container")

eventHub.addEventListener("click", (eventObject) => {
  if (eventObject.target.id.startsWith("delete-note")) {
    const idToDelete = eventObject.target.id.split("--")[1]
    // ---------- Write your code here -------------//
    // Call the deleteNote function and pass in the appropriate id
    // Then call NoteList to refresh the list of notes
  }
});

```

## Discussion Questions

Once you have delete working, go back through and try to answer these questions. Come prepared to discuss your ideas with the group. It's ok if you don't know the answers to these questions-- that's a good indication that you should find an instructor and chat with them about this chapter. 
1. What is different between POST and DELETE fetch calls?
2. How are the save and delete buttons utilized differently? Why?
