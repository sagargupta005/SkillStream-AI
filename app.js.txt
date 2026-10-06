let selectedTopic = "Python";

function showScreen(screenId) {

    document.querySelectorAll(".screen").forEach(screen => {
        screen.classList.remove("active");
    });

    document.getElementById(screenId).classList.add("active");
}

function selectTopic(topic) {

    selectedTopic = topic;

    document.querySelectorAll(".topic").forEach(button => {
        button.classList.remove("selected");
    });

    event.currentTarget.classList.add("selected");
}

function startLesson() {

    const title = document.getElementById("lessonTitle");
    const text = document.getElementById("lessonText");

    title.textContent = selectedTopic + " Fundamentals";

    const lessons = {

        "Python":
            "Python is a high-level programming language known for its simple and readable syntax. It is widely used for automation, web development, data science, and artificial intelligence.",

        "Java":
            "Java is an object-oriented programming language designed around portability, reliability, and reusable software components.",

        "Mechanical Engineering":
            "Mechanical engineering combines mechanics, materials, manufacturing, and design to create machines and useful physical systems.",

        "Data Science":
            "Data science combines statistics, programming, and machine learning to extract useful insights from structured and unstructured data."
    };

    text.textContent = lessons[selectedTopic];

    showScreen("lesson");
}

function answer(button, correct) {

    document.querySelectorAll(".answers button").forEach(btn => {
        btn.style.borderColor = "#30465e";
    });

    button.style.borderColor = correct ? "#63d7ff" : "#ff6b6b";

    const result = document.getElementById("quizResult");

    if (correct) {

        result.textContent =
            "✓ Correct! Great job. Your progress has been updated.";

        setTimeout(() => {
            showScreen("progressScreen");
        }, 1200);

    } else {

        result.textContent =
            "Not quite. Try again and review the lesson.";
    }
}
