# avg_scast
Average program from screencast

The point behind this video (and this code) is to demonstrate the basic use of `try!` and explain how implementing the `From` trait can make it more ergonomic when used with your own error types.

One thing I left out of this video is the fact that, at present, Rust does not allow you to write a generic, catch-all implementation of From, e.g.

	impl From<E: Error> for AppError {
		fn from(error: E) -> AppError {
			AppError {
				message: error.description()
			}
		}
	}

This is because rustc is not able to prove to itself that you're not converting *from* `AppError` *to* `AppError`. I *believe* this is being worked on, and this did work at one point in time, but something change in the way these things are constrained and we'll have to wait and see how this is handled going forward.
