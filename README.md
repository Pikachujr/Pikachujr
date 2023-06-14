- 👋 Hi, I’m @Pikachujr
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Pikachujr/Pikachujr is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

using UnityEngine;

public class MotorcycleController : MonoBehaviour
{
    public float speed = 10f;
    public float rotationSpeed = 100f;

    private Rigidbody rb;

    private void Awake()
    {
        rb = GetComponent<Rigidbody>();
    }

    private void FixedUpdate()
    {
        float moveInput = Input.GetAxis("Vertical");
        float rotationInput = Input.GetAxis("Horizontal");

        Move(moveInput);
        Rotate(rotationInput);
    }

    private void Move(float input)
    {
        Vector3 movement = transform.forward * input * speed * Time.fixedDeltaTime;
        rb.MovePosition(rb.position + movement);
    }

    private void Rotate(float input)
    {
        Quaternion rotation = Quaternion.Euler(0f, input * rotationSpeed * Time.fixedDeltaTime, 0f);
        rb.MoveRotation(rb.rotation * rotation);
    }
}
